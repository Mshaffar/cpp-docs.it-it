---
title: Creazione di operazioni asincrone in C , per le app UWPCreating Asynchronous Operations in C' for UWP Apps
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 635a8c95a3801c6e88feff1cefa3ed27727a8f88
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032187"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Creazione di operazioni asincrone in C , per le app UWPCreating Asynchronous Operations in C' for UWP Apps

Questo documento descrive alcuni dei punti chiave da tenere presenti quando usi la classe di attività per produrre operazioni asincrone basate su Windows ThreadPool in un'app UWP (Universal Windows Runtime).

L'uso della programmazione asincrona è un componente chiave nel modello di app di Windows Runtime perché consente alle app di rimanere reattive all'input dell'utente. È possibile avviare un'attività di lunga durata senza bloccare il thread dell'interfaccia utente e ricevere i risultati dell'attività in un secondo momento. È anche possibile annullare attività e ricevere notifiche di stato come attività in esecuzione in background. Il documento Programmazione asincrona [in C,](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) offre una panoramica del modello asincrono che è disponibile in Visual C. Questo documento insegna come usare e creare catene di operazioni asincrone di Windows Runtime. Questa sezione descrive come usare i tipi in ppltasks.h per produrre operazioni asincrone che possono essere usate da un altro componente di Windows Runtime e come controllare la modalità di esecuzione del lavoro asincrono. Prendi in considerazione anche la lettura di modelli di [programmazione e suggerimenti asincroni in Hilo (app](/previous-versions/windows/apps/jj160321(v=win.10)) di Windows Store che usano C e XAML) per scoprire come abbiamo usato la classe di attività per implementare operazioni asincrone in Hilo, un'app di Windows Runtime che usa C e XAML.

> [!NOTE]
> È possibile usare la libreria PPL [(Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md) e la [libreria di agenti asincroni](../../parallel/concrt/asynchronous-agents-library.md) in un'app UWP. Non è tuttavia possibile usare l'Utilità di pianificazione o Gestione risorse. In questo documento vengono descritte le funzionalità aggiuntive fornite dalla libreria PPL disponibili solo per un'app UWP e non per un'app desktop.

## <a name="key-points"></a>Punti chiave

- Usare [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) per creare operazioni asincrone che possono essere usate da altri componenti, che potrebbero essere scritti in linguaggi diversi da C++.

- Usare [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) per segnalare le notifiche di stato ai componenti che chiamano le operazioni asincrone.

- Usare i token di annullamento per permettere l'annullamento delle operazioni asincrone interne.

- Il comportamento della funzione `create_async` dipende dal tipo restituito della funzione lavoro che viene passata ad essa. Una funzione lavoro che restituisce un'attività ( `task<T>` o `task<void>`) viene eseguita in modo sincrono nel contesto che ha chiamato `create_async`. Una funzione lavoro che restituisce `T` o `void` viene eseguita in un contesto arbitrario.

- È possibile usare il metodo [concurrency::task::then](reference/task-class.md#then) per creare una catena di attività eseguite una dopo l'altra. In un'app UWP, il contesto predefinito per le continuazioni di un'attività dipende da come è stata costruita l'attività. Se l'attività è stata creata passando un'azione asincrona al costruttore di attività oppure passando un'espressione lambda che restituisce un'azione asincrona, il contesto predefinito per tutte le continuazioni dell'attività sarà il contesto corrente. Se l'attività non viene costruita da un'azione asincrona, per impostazione predefinita viene utilizzato un contesto arbitrario per le continuazioni dell'attività. È possibile eseguire l'override del contesto predefinito con la classe [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) .

## <a name="in-this-document"></a>In questo documento

- [Creazione di operazioni asincrone](#create-async)

- [Esempio: Creazione di un componente Windows Runtime C++](#example-component)

- [Controllo del thread di esecuzione](#exethread)

- [Esempio: controllo dell'esecuzione in un'app di Windows Runtime con C e XAML](#example-app)

## <a name="creating-asynchronous-operations"></a><a name="create-async"></a>Creazione di operazioni asincroneCreating Asynchronous Operations

È possibile usare il modello di attività e continuazione nella libreria PPL (Parallel Patterns Library) per definire le attività in background, oltre ad attività aggiuntive eseguite al completamento dell'attività precedente. Questa funzionalità viene fornita dalla classe [concurrency::task](../../parallel/concrt/reference/task-class.md) . Per altre informazioni su questo modello e sulla classe `task` , vedere [Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Windows Runtime è un'interfaccia di programmazione che puoi usare per creare app UWP che vengono eseguite solo in un ambiente speciale del sistema operativo. Tali app usano funzioni, tipi di dati e dispositivi autorizzati e vengono distribuite da Microsoft Store. Windows Runtime è rappresentato dall'interfaccia ABI *(Application Binary Interface).* L'interfaccia ABI è un contratto binario sottostante che rende le API di Windows Runtime disponibili per i linguaggi di programmazione, ad esempio Visual C.

Usando Windows Runtime, puoi usare le migliori funzionalità di vari linguaggi di programmazione e combinarle in un'unica app. È ad esempio possibile creare l'interfaccia utente in JavaScript ed eseguire la logica app che richiede attività di calcolo complesse in un componente C++. La possibilità di eseguire queste operazioni che richiedono attività di calcolo complesse in background è un fattore essenziale per mantenere reattiva l'interfaccia utente. Dal `task` fatto che la classe è specifica di C, è necessario usare un'interfaccia di Windows Runtime per comunicare operazioni asincrone ad altri componenti (che potrebbero essere scritti in linguaggi diversi da C. Windows Runtime fornisce quattro interfacce che è possibile utilizzare per rappresentare operazioni asincrone:The Windows Runtime provides four interfaces that you can use to represent asynchronous operations:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Rappresenta un'azione asincrona.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](/uwp/api/windows.foundation.iasyncactionwithprogress-1)<br/>
Rappresenta un'azione asincrona che segnala lo stato di avanzamento.

[Windows::Foundation::IAsyncOperation\<TResult>](/uwp/api/windows.foundation.iasyncoperation-1)<br/>
Rappresenta un'operazione asincrona che restituisce un risultato.

[Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](/uwp/api/windows.foundation.iasyncoperationwithprogress-2)<br/>
Rappresenta un'operazione asincrona che restituisce un risultato e segnala lo stato.

Il concetto di *azione* indica che un'attività asincrona non produce alcun valore, analogamente a una funzione che restituisce `void`. Il concetto di *operazione* indica che l'attività asincrona produce un valore. Il concetto di *stato* indica che l'attività può inviare messaggi di stato al chiamante. JavaScript, .NET Framework e Visual C++ offrono un modo specifico per creare istanze di queste interfacce da usare oltre i limiti dell'ABI. Per Visual C++ la libreria PPL fornisce la funzione [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) . Questa funzione crea un'operazione o un'operazione asincrona di Windows Runtime che rappresenta il completamento di un'attività. La `create_async` funzione accetta una funzione di lavoro (in `task` genere un'espressione lambda), crea internamente un oggetto ed esegue il wrapping di tale attività in una delle quattro interfacce asincrone di Windows Runtime.The function takes a work function (typically a lambda expression), internally creates a object, and wraps that task in one of the four asynchronous Windows Runtime interfaces.

> [!NOTE]
> Utilizzare `create_async` solo quando è necessario creare funzionalità a cui è possibile accedere da un'altra lingua o da un altro componente di Windows Runtime. Usare direttamente la classe `task` quando si è certi che l'operazione viene prodotta e utilizzata da codice C++ nello stesso componente.

Il tipo restituito di `create_async` viene determinato dal tipo dei rispettivi argomenti. Se, ad esempio, la funzione lavoro non restituisce alcun valore e non segnala lo stato, `create_async` restituirà `IAsyncAction`. Se la funzione lavoro non restituisce alcun valore ma segnala lo stato, `create_async` restituirà `IAsyncActionWithProgress`. Per segnalare lo stato, fornire un oggetto [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) come parametro per la funzione lavoro. La possibilità di segnalare lo stato permette di segnalare la quantità di lavoro eseguita e la quantità rimanente, ad esempio sotto forma di percentuale. Permette anche di segnalare i risultati non appena disponibili.

Le interfacce `IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>`e `IAsyncActionOperationWithProgress<TProgress, TProgress>` forniscono un metodo `Cancel` che permette di annullare l'operazione asincrona. La classe `task` può essere usata con i token di annullamento. Quando si usa un token di annullamento per annullare il lavoro, il runtime non avvia nuovo lavoro che sottoscrive tale token. Il lavoro già attivo è in grado di monitorare l'annullamento e arrestarsi quando possibile. Questo meccanismo è descritto in modo più dettagliato nel documento [Cancellation in the PPL](cancellation-in-the-ppl.md). Puoi connettere l'annullamento`Cancel` delle attività con i metodi di Windows Runtime in due modi. È prima di tutto possibile definire la funzione lavoro passata a `create_async` in modo che accetti un oggetto [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) . Quando `Cancel` viene chiamato il metodo , questo token di annullamento `task` viene annullato `create_async` e le normali regole di annullamento si applicano all'oggetto sottostante che supporta la chiamata. Se non si specifica un oggetto `cancellation_token` , l'oggetto `task` sottostante ne definirà uno implicitamente. Definire un oggetto `cancellation_token` quando è necessario rispondere in modo cooperativo all'annullamento nella funzione lavoro. La sezione [Esempio: controllo dell'esecuzione in un'app](#example-app) di Windows Runtime con C e XAML mostra un esempio di come eseguire l'annullamento in un'app UWP (Universal Windows Platform) con C'è e XAML che usa un componente personalizzato di Windows Runtime in C.

> [!WARNING]
> In una catena di continuazioni di attività, pulire sempre lo stato e quindi chiamare [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) quando il token di annullamento viene annullato. Se si esce prima di chiamare `cancel_current_task`, l'operazione passa allo stato completato invece che allo stato annullato.

La tabella seguente riepiloga le combinazioni che possono essere usate per definire operazioni asincrone nell'app.

|Per creare questa interfaccia di Windows RuntimeTo create this Windows Runtime interface|Restituire questo tipo da `create_async`|Passare questi tipi di parametro alla funzione lavoro per usare implicitamente il token di annullamento|Passare questi tipi di parametro alla funzione lavoro per usare esplicitamente il token di annullamento|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` o `task<void>`|(nessuna)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` o `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` o `task<T>`|(nessuna)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` o `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

È possibile restituire un valore o un oggetto `task` dalla funzione lavoro passata alla funzione `create_async` . Queste variazioni producono comportamenti diversi. Quando viene restituito un valore, la funzione lavoro viene sottoposta a wrapping in `task` in modo che possa essere eseguita su una thread in background. L'oggetto `task` sottostante usa inoltre un token di annullamento implicito. Se invece viene restituito un oggetto `task` , la funzione lavoro viene eseguita in modo sincrono. Se quindi viene restituito un oggetto `task` , assicurarsi che tutte le operazioni lunghe nella funzione lavoro possano essere eseguite come attività per mantenere la reattività dell'applicazione. L'oggetto `task` sottostante inoltre non usa un token di annullamento implicito. È quindi necessario definire la funzione lavoro in modo che accetti un oggetto `cancellation_token` se è necessario il supporto per l'annullamento quando si restituisce un oggetto `task` da `create_async`.

L'esempio seguente mostra i `IAsyncAction` vari modi per creare un oggetto che può essere utilizzato da un altro componente di Windows Runtime.The following example shows the various ways to create an object that can be consumed by another Windows Runtime component.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

## <a name="example-creating-a-c-windows-runtime-component-and-consuming-it-from-c"></a><a name="example-component"></a>Esempio: creazione di un componente di Windows Runtime di C e utilizzo da C\#

Si consideri un'app che usa XAML e C' per definire l'interfaccia utente e un componente di Windows Runtime c'è per eseguire operazioni che richiedono un utilizzo intensivo del calcolo. In questo esempio il componente C++ calcola i numeri primi di un intervallo specifico. Per illustrare le differenze tra le quattro interfacce di attività asincrone di `Primes`Windows Runtime, avviare, in Visual Studio, creando una soluzione **vuota** e denominandola . Aggiungere quindi un progetto **Componente Windows Runtime** alla soluzione e denominarlo `PrimesLibrary`. Aggiungere il codice seguente al file di intestazione C++ generato. Questo esempio rinomina Class1.h in Primes.h. Ogni metodo `public` definisce una delle quattro interfacce asincrone. I metodi che restituiscono un valore restituiscono un oggetto [Windows::Foundation::Collections::IVector\<int>.](/uwp/api/windows.foundation.collections.ivector-1) I metodi che segnalano lo stato producono valori `double` che definiscono la percentuale di lavoro complessivo completata.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
> Per convenzione, i nomi dei metodi asincroni in Windows Runtime in genere terminano con "Async".

Aggiungere il codice seguente al file di origine C++ generato. Questo esempio rinomina Class1.cpp in Primes.cpp. La funzione `is_prime` determina se l'input è un numero primo. I metodi rimanenti implementano la classe `Primes` . Ogni chiamata a `create_async` usa una firma compatibile con il metodo da cui viene effettuata la chiamata. Ad esempio, poiché `Primes::ComputePrimesAsync` restituisce `IAsyncAction`, la funzione lavoro fornita a `create_async` non restituisce alcun valore e non accetta alcun oggetto `progress_reporter` come parametro.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Ogni metodo esegue prima la convalida per garantire che i parametri di input non siano negativi. Se un valore di input è negativo, il metodo genera un'eccezione [Platform::InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md). La gestione degli errori viene illustrata più avanti in questa sezione.

Per usare questi metodi da un'app UWP, usa il modello **di app vuota (XAML)** di Visual C' per aggiungere un secondo progetto alla soluzione di Visual Studio. Questo esempio assegna al progetto il nome `Primes`. Dal progetto `Primes` aggiungere un riferimento al progetto `PrimesLibrary` .

Aggiungere il codice seguente a MainPage.xaml. Questo codice definisce l'interfaccia utente, in modo da permettere la chiamata del componente C++ e la visualizzazione dei risultati.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Aggiungere il codice seguente alla classe `MainPage` in MainPage.xaml. Questo codice definisce un oggetto `Primes` e i gestori eventi del pulsante.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Questi metodi usano le parole chiave `async` e `await` per aggiornare l'interfaccia utente dopo il completamento delle operazioni asincrone. Per informazioni sulla codifica asincrona nelle app UWP, vedere [Threading e programmazione asincrona](/windows/uwp/threading-async).

I metodi `getPrimesCancellation` e `cancelGetPrimes` interagiscono per permettere all'utente di annullare l'operazione. Quando l'utente **Cancel** sceglie il `cancelGetPrimes` annulla pulsante, il metodo chiama [IAsyncOperationWithProgress\<TResult, TProgress>::Annulla](/uwp/api/windows.foundation.iasyncinfo.cancel) per annullare l'operazione. Il runtime di concorrenza, che gestisce l'operazione asincrona sottostante, genera un tipo di eccezione interna intercettato da Windows Runtime per comunicare che l'annullamento è stato completato. Per ulteriori informazioni sul modello di [annullamento,](../../parallel/concrt/cancellation-in-the-ppl.md)vedere Annullamento .

> [!IMPORTANT]
> Per consentire alla libreria PPL di segnalare correttamente a Windows Runtime che ha annullato l'operazione, non intercettare questo tipo di eccezione interna. Ciò significa che è necessario non intercettare tutte le eccezioni (`catch (...)`). Se è necessario intercettare tutte le eccezioni, generare nuovamente l'eccezione per assicurarsi che Windows Runtime possa completare l'operazione di annullamento.

La figura seguente mostra l'app `Primes` dopo che ogni opzione è stata selezionata.

![App Prime di Windows Runtime](../../parallel/concrt/media/concrt_windows_primes.png "App Prime di Windows Runtime")

Per esempi in cui viene usato `create_async` per creare attività asincrone che possono essere utilizzate da altri linguaggi, vedere [Utilizzo di C++ nell'esempio di utilità di ottimizzazione dei viaggi di Bing Mappe](/previous-versions/windows/apps/hh699891(v=vs.140)) e [Windows 8 Asynchronous Operations in C++ with PPL](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d)(Operazioni asincrone di Windows 8 in C++ con PPL).

## <a name="controlling-the-execution-thread"></a><a name="exethread"></a>Controllo del thread di esecuzioneControlling the Execution Thread

Windows Runtime usa il modello di threading COM. In questo modello gli oggetti vengono ospitati in diversi apartment, in base al modo in cui gestiscono la rispettiva sincronizzazione. Gli oggetti thread-safe vengono ospitati nell'apartment a thread multipli (MTA, Multi-Threaded Apartment). Gli oggetti a cui deve accedere un singolo thread vengono ospitati in un apartment a thread singolo (STA, Single-Threaded Apartment).

In un'app che ha un'interfaccia utente, il thread ASTA (Application STA) è responsabile per la distribuzione dei messaggi della finestra ed è l'unico thread nel processo in grado di aggiornare i controlli dell'interfaccia utente ospitati nell'apartment a thread singolo. Questo comportamento ha due conseguenze. Per abilitare l'app in modo che rimanga reattiva, è prima di tutto necessario che tutte le operazioni a utilizzo elevato di CPU e le operazioni I/O non vengano eseguite nel thread ASTA. È quindi necessario eseguire di nuovo il marshaling dei thread di background nel thread ASTA per aggiornare l'interfaccia utente. In un'app UWP `MainPage` di C, e in altre pagine XAML, vengono tutte eseguite nell'ATSA. Le continuazioni delle attività dichiarate nel thread ASTA vengono quindi eseguite in tale thread per impostazione predefinita. Sarà quindi possibile aggiornare i controlli direttamente nel corpo della continuazione. Se tuttavia si annida un'attività in un'altra attività, eventuali continuazioni in tale attività annidata verranno eseguite nell'apartment a thread multipli. È quindi necessario valutare se specificare in modo esplicito il contesto in cui devono essere eseguite le continuazioni.

Un'attività creata da un'operazione asincrona, ad esempio `IAsyncOperation<TResult>`, usa una semantica speciale che permette di ignorare i dettagli relativi al threading. Anche se è possibile che un'operazione venga eseguita in un thread in background o che non sia supportata da alcun thread, per impostazione predefinita le rispettive continuazioni verranno eseguite nell'apartment che ha avviato le operazioni di continuazione, ovvero l'apartment che ha chiamato `task::then`). È possibile usare la classe [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) per controllare il contesto di esecuzione di una continuazione. Usare questi metodi di helper statici per creare oggetti `task_continuation_context` :

- Usare [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) per specificare che la continuazione verrà eseguita in un thread in background.

- Usare [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) per specificare che la continuazione verrà eseguita nel thread che ha chiamato `task::then`.

È possibile passare un oggetto `task_continuation_context` al metodo [task::then](reference/task-class.md#then) per controllare in modo esplicito il contesto di esecuzione della continuazione oppure passare l'attività a un altro apartment e quindi chiamare il metodo `task::then` per controllare in modo implicito il contesto di esecuzione.

> [!IMPORTANT]
> Poiché il thread principale dell'interfaccia utente delle app UWP viene eseguito in STA, le continuazioni create in tale STA per impostazione predefinita vengono eseguite in STA. Le continuazioni create nell'apartment a thread multipli verranno di conseguenza eseguite nell'apartment a thread multipli.

La sezione seguente illustra un'app che legge un file da disco, individua le parole più comuni in tale file e quindi mostra i risultati nell'interfaccia utente. L'operazione finale, l'aggiornamento dell'interfaccia utente, si verifica nel thread dell'interfaccia utente.

> [!IMPORTANT]
> Questo comportamento è specifico per le app UWP. Per le app desktop non è possibile controllare la posizione in cui vengono eseguite le continuazioni. L'Utilità di pianificazione sceglie invece un thread di lavoro in cui eseguire ogni continuazione.

> [!IMPORTANT]
> Non chiamare [concurrency::task::wait](reference/task-class.md#wait) nel corpo di una continuazione che viene eseguita nell'apartment a thread singolo. In caso contrario, il runtime genera [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) poiché questo metodo blocca il thread corrente e può provocare la mancata risposta da parte dell'app. È tuttavia possibile chiamare il metodo [concurrency::task::get](reference/task-class.md#get) per ricevere il risultato dell'attività antecedente in una continuazione basata su attività.

## <a name="example-controlling-execution-in-a-windows-runtime-app-with-c-and-xaml"></a><a name="example-app"></a>Esempio: controllo dell'esecuzione in un'app di Windows Runtime con C e XAML

Si consideri un'app XAML C++ che legge un file da disco, individua le parole più comuni in tale file e quindi mostra i risultati nell'interfaccia utente. Per creare questa app, avviare, in Visual Studio, creando un `CommonWords`progetto di applicazione vuota **(Windows universale)** e denominandolo . Nel manifesto dell'app specificare la capacità **Raccolta documenti** per permettere all'app di accedere alla cartella Documenti. Aggiungere anche il tipo di file di testo (con estensione txt) alla sezione relativa alle dichiarazioni nel manifesto dell'app. Per altre informazioni sulle funzionalità e le dichiarazioni delle app, vedere [Creazione di pacchetti, distribuzione e query di app di Windows.](/windows/win32/appxpkg/appx-portal)

Aggiornare l'elemento `Grid` in MainPage.xaml per includere un elemento `ProgressRing` e un elemento `TextBlock` . L'elemento `ProgressRing` indica che l'operazione è in corso e `TextBlock` mostra i risultati del calcolo.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Aggiungere le `#include` seguenti istruzioni a *pch.h*.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Aggiungere le dichiarazioni del metodo seguente alla classe `MainPage` (MainPage.h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Aggiungere le istruzioni `using` seguenti a MainPage.cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

In MainPage.cpp implementare i metodi `MainPage::MakeWordList`, `MainPage::FindCommonWords`e `MainPage::ShowResults` . `MainPage::MakeWordList` e `MainPage::FindCommonWords` eseguono operazioni a utilizzo elevato di calcolo. Il metodo `MainPage::ShowResults` visualizza il risultato del calcolo nell'interfaccia utente.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Modificare il costruttore `MainPage` per creare una catena di attività di continuazione che visualizza nell'interfaccia utente le parole comuni rilevate nel libro *Iliade* di Omero. Le prime due attività di continuazione, che suddividono il testo in singole parole e trovano le parole comuni, possono richiedere molto tempo e sono quindi configurate per l'esecuzione in background. L'attività di continuazione finale, che aggiorna l'interfaccia utente, non specifica alcun contesto di continuazione e quindi segue le regole di threading dell'apartment .

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
> Questo esempio illustra come specificare i contesti di esecuzione e come creare una catena di continuazioni. È importante ricordare che per impostazione predefinita un'attività creata da un'operazione asincrona esegue le rispettive continuazione nell'apartment che ha chiamato `task::then`. Questo esempio usa quindi `task_continuation_context::use_arbitrary` per specificare che le operazioni che non coinvolgono l'interfaccia utente vengano eseguite in un thread in background.

La figura seguente mostra i risultati dell'app `CommonWords` .

![App CommonWords di Windows Runtime](../../parallel/concrt/media/concrt_windows_common_words.png "App CommonWords di Windows Runtime")

In questo esempio, è possibile supportare `task` l'annullamento perché gli oggetti che supportano `create_async` utilizzano un token di annullamento implicito. Definire la funzione lavoro in modo che accetti un oggetto `cancellation_token` se l'attività deve rispondere all'annullamento in modo cooperativo. Per altre informazioni sull'annullamento nella libreria PPL, vedere [Cancellation in the PPL](cancellation-in-the-ppl.md).

## <a name="see-also"></a>Vedere anche

[Runtime di concorrenzaConcurrency Runtime](../../parallel/concrt/concurrency-runtime.md)
