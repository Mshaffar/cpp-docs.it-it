---
title: Blocchi dei messaggi asincroni
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: ef6f6f56a82cc76c2c270817ed40d15418960dc1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141951"
---
# <a name="asynchronous-message-blocks"></a>Blocchi dei messaggi asincroni

La libreria di agenti fornisce diversi tipi di blocchi di messaggi che consentono di propagare i messaggi tra i componenti dell'applicazione in modo thread-safe. Questi tipi di blocchi di messaggi vengono spesso utilizzati con le varie routine di passaggio dei messaggi, ad esempio [Concurrency:: Send](reference/concurrency-namespace-functions.md#send), [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend), [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive)e [Concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive). Per ulteriori informazioni sulle routine di passaggio dei messaggi definite dalla libreria di agenti, vedere [Message Passing Functions](../../parallel/concrt/message-passing-functions.md).

## <a name="top"></a> Sezioni

In questo argomento sono incluse le sezioni seguenti:

- [Origini e destinazioni](#sources_and_targets)

- [Propagazione messaggi](#propagation)

- [Panoramica dei tipi di blocchi di messaggi](#overview)

- [Classe unbounded_buffer](#unbounded_buffer)

- [Classe overwrite_buffer](#overwrite_buffer)

- [Classe single_assignment](#single_assignment)

- [Classe call](#call)

- [Classe transformer](#transformer)

- [Classe choice](#choice)

- [Classi join e multitype_join](#join)

- [Classe timer](#timer)

- [Filtro messaggi](#filtering)

- [Prenotazione messaggi](#reservation)

## <a name="sources_and_targets"></a>Origini e destinazioni

Le origini e le destinazioni sono due importanti partecipanti al passaggio del messaggio. Un' *origine* fa riferimento a un endpoint di comunicazione che invia messaggi. Una *destinazione* fa riferimento a un endpoint di comunicazione che riceve i messaggi. È possibile pensare a un'origine come a un endpoint letto da e a una destinazione come endpoint in cui si scrive. Le applicazioni connettono le origini e le destinazioni per formare le *reti di messaggistica*.

La libreria di agenti usa due classi astratte per rappresentare origini e destinazioni: [Concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) e [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md). I tipi di blocchi di messaggi che fungono da origini derivano da `ISource`; i tipi di blocchi di messaggi che fungono da destinazioni derivano da `ITarget`. I tipi di blocchi di messaggi che fungono da origini e destinazioni derivano da `ISource` e `ITarget`.

[[Torna all'inizio](#top)]

## <a name="propagation"></a>Propagazione messaggi

La *propagazione dei messaggi* è l'azione di invio di un messaggio da un componente a un altro. Quando a un blocco di messaggi viene offerto un messaggio, il messaggio può essere accettato, rifiutato o posticipato. Ogni tipo di blocco di messaggi archivia e trasmette i messaggi in modi diversi. Ad esempio, la classe `unbounded_buffer` archivia un numero illimitato di messaggi, la classe `overwrite_buffer` archivia un singolo messaggio alla volta e la classe transformer archivia una versione modificata di ogni messaggio. Questi tipi di blocchi di messaggi sono descritti in modo più dettagliato più avanti in questo documento.

Quando un blocco di messaggi accetta un messaggio, può facoltativamente eseguire il lavoro e, se il blocco del messaggio è un'origine, passare il messaggio risultante a un altro membro della rete. Un blocco di messaggio può utilizzare una funzione di filtro per rifiutare i messaggi che non si desidera ricevere. I filtri sono descritti in modo più dettagliato più avanti in questo argomento, nella sezione [filtro messaggi](#filtering). Un blocco di messaggi che posticipa un messaggio può riservare il messaggio e utilizzarlo in un secondo momento. La prenotazione dei messaggi viene descritta in modo più dettagliato più avanti in questo argomento nella sezione [prenotazione messaggi](#reservation).

La libreria di agenti consente ai blocchi di messaggi di passare i messaggi in modo asincrono o sincrono. Quando si passa un messaggio a un blocco di messaggi in modo sincrono, ad esempio tramite la funzione `send`, il runtime blocca il contesto corrente fino a quando il blocco di destinazione non accetta o rifiuta il messaggio. Quando si passa un messaggio a un blocco di messaggi in modo asincrono, ad esempio usando la funzione `asend`, il runtime fornisce il messaggio alla destinazione e se la destinazione accetta il messaggio, il runtime pianifica un'attività asincrona che propaga il messaggio al destinatario. Il runtime usa le attività leggere per propagare i messaggi in modo cooperativo. Per ulteriori informazioni sulle attività leggere, vedere [utilità di pianificazione](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Le applicazioni connettono le origini e le destinazioni per formare le reti di messaggistica. In genere, si collega la rete e si chiama `send` o `asend` per passare i dati alla rete. Per connettere un blocco di messaggi di origine a una destinazione, chiamare il metodo [Concurrency:: ISource:: link_target](reference/isource-class.md#link_target) . Per disconnettere un blocco di origine da una destinazione, chiamare il metodo [Concurrency:: ISource:: unlink_target](reference/isource-class.md#unlink_target) . Per disconnettere un blocco di origine da tutte le relative destinazioni, chiamare il metodo [Concurrency:: ISource:: unlink_targets](reference/isource-class.md#unlink_targets) . Quando uno dei tipi di blocchi di messaggi predefiniti lascia l'ambito o viene eliminato definitivamente, si disconnette automaticamente da qualsiasi blocco di destinazione. Alcuni tipi di blocchi di messaggi limitano il numero massimo di destinazioni in cui è possibile scrivere. Nella sezione seguente vengono descritte le restrizioni che si applicano ai tipi di blocchi di messaggi predefiniti.

[[Torna all'inizio](#top)]

## <a name="overview"></a>Panoramica dei tipi di blocchi di messaggi

Nella tabella seguente viene brevemente descritto il ruolo dei principali tipi di blocchi di messaggi.

[unbounded_buffer](#unbounded_buffer)<br/>
Archivia una coda di messaggi.

[overwrite_buffer](#overwrite_buffer)<br/>
Archivia un messaggio che può essere scritto e letto più volte.

[single_assignment](#single_assignment)<br/>
Archivia un messaggio che può essere scritto in una sola volta e letto più volte.

[chiamare](#call)<br/>
Esegue operazioni quando riceve un messaggio.

[trasformatore](#transformer)<br/>
Esegue operazioni quando riceve dati e invia il risultato di tale operazione a un altro blocco di destinazione. La classe `transformer` può agire su diversi tipi di input e output.

[scelta](#choice)<br/>
Seleziona il primo messaggio disponibile da un set di origini.

[join e join multitipo](#join)<br/>
Attendere che tutti i messaggi vengano ricevuti da un set di origini e quindi combinare i messaggi in un messaggio per un altro blocco di messaggi.

[timer](#timer)<br/>
Invia un messaggio a un blocco di destinazione a intervalli regolari.

Questi tipi di blocchi di messaggi presentano caratteristiche diverse che li rendono utili per situazioni diverse. Di seguito sono riportate alcune delle caratteristiche:

- *Tipo di propagazione*: indica se il blocco del messaggio funge da origine dati, destinatario di dati o entrambi.

- *Ordinamento dei messaggi*: indica se il blocco di messaggi mantiene l'ordine originale in cui i messaggi vengono inviati o ricevuti. Ogni tipo di blocco di messaggi predefinito mantiene l'ordine originale in cui invia o riceve messaggi.

- *Conteggio origine*: numero massimo di origini da cui il blocco del messaggio può leggere.

- *Target count*: numero massimo di destinazioni in cui è possibile scrivere il blocco del messaggio.

Nella tabella seguente viene illustrato il modo in cui queste caratteristiche sono correlate ai vari tipi di blocchi di messaggi.

|Tipo di blocco messaggio|Tipo di propagazione (origine, destinazione o entrambi)|Ordinamento messaggi (ordinato o non ordinato)|Conteggio origine|Conteggio destinazione|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Entrambe|Ordinato|Unbounded|Unbounded|
|`overwrite_buffer`|Entrambe|Ordinato|Unbounded|Unbounded|
|`single_assignment`|Entrambe|Ordinato|Unbounded|Unbounded|
|`call`|Destinazione|Ordinato|Unbounded|Non applicabile|
|`transformer`|Entrambe|Ordinato|Unbounded|1|
|`choice`|Entrambe|Ordinato|10|1|
|`join`|Entrambe|Ordinato|Unbounded|1|
|`multitype_join`|Entrambe|Ordinato|10|1|
|`timer`|Source (Sorgente)|Non applicabile|Non applicabile|1|

Le sezioni seguenti descrivono i tipi di blocchi di messaggi in modo più dettagliato.

[[Torna all'inizio](#top)]

## <a name="unbounded_buffer"></a>Classe unbounded_buffer

La classe [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) rappresenta una struttura di messaggistica asincrona per utilizzo generico. Questa classe archivia una coda di messaggi FIFO (First In, First Out) che possono essere letti da più destinazioni o in cui possono scrivere più origini. Quando una destinazione riceve un messaggio da un oggetto `unbounded_buffer`, il messaggio viene rimosso dalla coda di messaggi. Pertanto, sebbene un oggetto `unbounded_buffer` possa avere più destinazioni, ogni messaggio viene ricevuto da una sola destinazione. La classe `unbounded_buffer` è utile quando si vogliono passare più messaggi a un altro componente e tale componente deve ricevere ogni messaggio.

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `unbounded_buffer`. In questo esempio vengono inviati tre valori a un oggetto `unbounded_buffer`, quindi tali valori vengono letti dallo stesso oggetto.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
334455
```

Per un esempio completo in cui viene illustrato come usare la classe `unbounded_buffer`, vedere [procedura: implementare vari modelli producer-consumer](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Torna all'inizio](#top)]

## <a name="overwrite_buffer"></a>Classe overwrite_buffer

La classe [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) è simile alla classe `unbounded_buffer`, ad eccezione del fatto che un oggetto `overwrite_buffer` archivia solo un messaggio. Inoltre, quando una destinazione riceve un messaggio da un oggetto `overwrite_buffer`, il messaggio non viene rimosso dal buffer. Pertanto, più destinazioni riceveranno una copia del messaggio.

La classe `overwrite_buffer` è utile quando si desidera passare più messaggi a un altro componente, ma il componente necessita solo del valore più recente. Questa classe è utile anche quando si vuole trasmettere un messaggio a più componenti.

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `overwrite_buffer`. In questo esempio vengono inviati tre valori a un oggetto `overwrite _buffer`, quindi viene letto il valore corrente dallo stesso oggetto tre volte. Questo esempio è simile all'esempio per la classe `unbounded_buffer`. Tuttavia, la classe `overwrite_buffer` archivia un solo messaggio. Inoltre, il runtime non rimuove il messaggio da un oggetto `overwrite_buffer` dopo che è stato letto.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
555555
```

Per un esempio completo in cui viene illustrato come usare la classe `overwrite_buffer`, vedere [procedura: implementare vari modelli producer-consumer](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Torna all'inizio](#top)]

## <a name="single_assignment"></a>Classe single_assignment

La classe [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) è simile alla classe `overwrite_buffer`, ad eccezione del fatto che un oggetto `single_assignment` può essere scritto in una sola volta. Come per la classe `overwrite_buffer`, quando da una destinazione riceve un messaggio da un oggetto `single_assignment`, il messaggio viene rimosso dalla coda di messaggi. Pertanto, più destinazioni riceveranno una copia del messaggio. La classe `single_assignment` è utile quando si desidera trasmettere un messaggio a più componenti.

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `single_assignment`. In questo esempio vengono inviati tre valori a un oggetto `single_assignment`, quindi viene letto il valore corrente dallo stesso oggetto tre volte. Questo esempio è simile all'esempio per la classe `overwrite_buffer`. Sebbene le classi `overwrite_buffer` e `single_assignment` memorizzino un singolo messaggio, la classe `single_assignment` può essere scritta una sola volta.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
333333
```

Per un esempio completo in cui viene illustrato come usare la classe `single_assignment`, vedere [procedura dettagliata: implementazione di future](../../parallel/concrt/walkthrough-implementing-futures.md).

[[Torna all'inizio](#top)]

## <a name="call"></a>Classe call

La classe [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) funge da ricevitore del messaggio che esegue una funzione lavoro quando riceve i dati. Questa funzione di lavoro può essere un'espressione lambda, un oggetto funzione o un puntatore a funzione. Un oggetto `call` si comporta in modo diverso rispetto a una normale chiamata di funzione perché agisce in parallelo con gli altri componenti che inviano messaggi a tale oggetto. Se un oggetto `call` sta eseguendo il lavoro quando riceve un messaggio, aggiunge tale messaggio a una coda. Ogni oggetto `call` elabora i messaggi in coda nell'ordine in cui vengono ricevuti.

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `call`. In questo esempio viene creato un oggetto `call` che stampa ogni valore che riceve nella console. Nell'esempio vengono quindi inviati tre valori all'oggetto `call`. Poiché l'oggetto `call` elabora i messaggi in un thread separato, in questo esempio vengono utilizzate anche una variabile contatore e un oggetto [evento](../../parallel/concrt/reference/event-class.md) per garantire che l'oggetto `call` elabori tutti i messaggi prima che la funzione `wmain` restituisca.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
334455
```

Per un esempio completo in cui viene illustrato come usare la classe `call`, vedere [procedura: fornire funzioni lavoro alle classi call e Transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[[Torna all'inizio](#top)]

## <a name="transformer"></a>Classe transformer

La classe [Concurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) funge sia da ricevitore del messaggio che da mittente del messaggio. La classe `transformer` è simile alla classe `call` perché esegue una funzione di lavoro definita dall'utente durante la ricezione dei dati. Tuttavia, la classe `transformer` invia anche il risultato della funzione lavoro agli oggetti Receiver. Analogamente a un oggetto `call`, un oggetto `transformer` agisce in parallelo con gli altri componenti che inviano messaggi a tale oggetto. Se un oggetto `transformer` sta eseguendo il lavoro quando riceve un messaggio, aggiunge tale messaggio a una coda. Ogni oggetto `transformer` elabora i messaggi in coda nell'ordine in cui vengono ricevuti.

La classe `transformer` invia il messaggio a una destinazione. Se si imposta il parametro `_PTarget` nel costruttore su `NULL`, è possibile specificare in un secondo momento la destinazione chiamando il metodo [Concurrency:: link_target](reference/source-block-class.md#link_target) .

A differenza di tutti gli altri tipi di blocchi di messaggi asincroni forniti dalla libreria di agenti, la classe `transformer` può agire su diversi tipi di input e output. Questa possibilità di trasformare i dati da un tipo a un altro rende la classe `transformer` un componente chiave in molte reti simultanee. Inoltre, è possibile aggiungere funzionalità parallele con granularità fine nella funzione lavoro di un oggetto `transformer`.

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `transformer`. In questo esempio viene creato un oggetto `transformer` che multipla ogni input `int` valore per 0,33 per produrre un valore `double` come output. Nell'esempio vengono quindi ricevuti i valori trasformati dallo stesso oggetto `transformer` e vengono stampati nella console.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
10.8914.5218.15
```

Per un esempio completo in cui viene illustrato come usare la classe `transformer`, vedere [procedura: usare Transformer in una pipeline di dati](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[[Torna all'inizio](#top)]

## <a name="choice"></a>Classe choice

La classe [Concurrency:: Choice](../../parallel/concrt/reference/choice-class.md) seleziona il primo messaggio disponibile da un set di origini. La classe `choice` rappresenta un meccanismo di flusso di controllo anziché un meccanismo di flusso di flussi di codice (l'argomento [libreria di agenti asincroni](../../parallel/concrt/asynchronous-agents-library.md) descrive le differenze tra il flusso dei flussi di controllo e il flusso di controllo).

La lettura da un oggetto choice è simile alla chiamata della funzione API Windows `WaitForMultipleObjects` quando il parametro `bWaitAll` è impostato su `FALSE`. Tuttavia, la classe `choice` associa i dati all'evento stesso anziché a un oggetto di sincronizzazione esterno.

In genere, si usa la classe `choice` insieme alla funzione [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) per guidare il flusso di controllo nell'applicazione. Utilizzare la classe `choice` quando è necessario selezionare tra i buffer dei messaggi con tipi diversi. Utilizzare la classe `single_assignment` quando è necessario selezionare tra i buffer dei messaggi che hanno lo stesso tipo.

L'ordine in cui si collegano le origini a un oggetto `choice` è importante perché consente di determinare il messaggio selezionato. Si consideri, ad esempio, il caso in cui si collegano più buffer di messaggi che contengono già un messaggio a un oggetto `choice`. L'oggetto `choice` seleziona il messaggio dalla prima origine a cui è collegato. Dopo aver collegato tutte le origini, l'oggetto `choice` conserva l'ordine in cui ogni origine riceve un messaggio.

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `choice`. In questo esempio viene utilizzata la funzione [Concurrency:: make_choice](reference/concurrency-namespace-functions.md#make_choice) per creare un oggetto `choice` che seleziona tra tre blocchi di messaggi. Nell'esempio vengono quindi calcolati diversi numeri di Fibonacci e ogni risultato viene archiviato in un blocco di messaggi diverso. Nell'esempio viene quindi stampato nella console un messaggio basato sull'operazione completata per prima.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Questo esempio produce l'output di esempio seguente:

```Output
fib35 received its value first. Result = 9227465
```

Poiché l'attività che calcola il numero di Fibonacci 35<sup>°</sup> non è garantita per prima, l'output di questo esempio può variare.

In questo esempio viene utilizzato l'algoritmo [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) per calcolare i numeri di Fibonacci in parallelo. Per ulteriori informazioni su `parallel_invoke`, vedere [algoritmi paralleli](../../parallel/concrt/parallel-algorithms.md).

Per un esempio completo in cui viene illustrato come usare la classe `choice`, vedere [procedura: selezionare tra le attività completate](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[[Torna all'inizio](#top)]

## <a name="join"></a>Classi join e multitype_join

Le classi [Concurrency:: join](../../parallel/concrt/reference/join-class.md) e [Concurrency:: multitype_join](../../parallel/concrt/reference/multitype-join-class.md) consentono di attendere la ricezione di un messaggio da parte di ogni membro di un set di origini. La classe `join` agisce sugli oggetti di origine che hanno un tipo di messaggio comune. La classe `multitype_join` agisce sugli oggetti di origine che possono avere tipi di messaggio diversi.

La lettura da un oggetto `join` o `multitype_join` è simile alla chiamata della funzione API Windows `WaitForMultipleObjects` quando il parametro `bWaitAll` è impostato su `TRUE`. Tuttavia, proprio come un oggetto `choice`, `join` e `multitype_join` oggetti utilizzano un meccanismo di evento che associa i dati all'evento stesso anziché a un oggetto di sincronizzazione esterno.

La lettura da un oggetto `join` produce un oggetto std::[vector](../../standard-library/vector-class.md) . La lettura da un oggetto `multitype_join` produce un oggetto std::[Tuple](../../standard-library/tuple-class.md) . Gli elementi vengono visualizzati in questi oggetti nello stesso ordine in cui i buffer di origine corrispondenti sono collegati all'oggetto `join` o `multitype_join`. Poiché l'ordine in cui si collegano i buffer di origine a un oggetto `join` o `multitype_join` è associato all'ordine degli elementi nell'oggetto `vector` o `tuple` risultante, si consiglia di non scollegare un buffer di origine esistente da un join. Questa operazione può causare un comportamento non specificato.

### <a name="greedy-versus-non-greedy-joins"></a>Join greedy e non greedy

Le classi `join` e `multitype_join` supportano il concetto di join greedy e non greedy. Un *join greedy* accetta un messaggio da ogni origine perché i messaggi diventano disponibili fino a quando non sono disponibili tutti i messaggi. Un *join non greedy* riceve i messaggi in due fasi. In primo luogo, un join non greedy attende fino a quando non viene offerto un messaggio da ogni origine. In secondo luogo, dopo che tutti i messaggi di origine sono disponibili, un join non greedy tenta di riservare ognuno di questi messaggi. Se può riservare ogni messaggio, utilizzerà tutti i messaggi e li propagherà nella destinazione. In caso contrario, rilascia o Annulla, le prenotazioni dei messaggi e attende di nuovo che ogni origine riceva un messaggio.

I join greedy offrono prestazioni migliori rispetto ai join non greedy perché accettano immediatamente i messaggi. In rari casi, tuttavia, i join greedy possono causare deadlock. Usare un join non greedy quando sono presenti più join che contengono uno o più oggetti di origine condivisi.

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `join`. In questo esempio viene utilizzata la funzione [Concurrency:: make_join](reference/concurrency-namespace-functions.md#make_join) per creare un `join` oggetto che riceve da tre oggetti `single_assignment`. In questo esempio vengono calcolati diversi numeri di Fibonacci, viene archiviato ogni risultato in un oggetto `single_assignment` diverso, quindi viene stampato nella console ogni risultato che l'oggetto `join` contiene. Questo esempio è simile all'esempio per la classe `choice`, ad eccezione del fatto che la classe `join` attende che tutti i blocchi di messaggi di origine ricevano un messaggio.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

In questo esempio viene utilizzato l'algoritmo [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) per calcolare i numeri di Fibonacci in parallelo. Per ulteriori informazioni su `parallel_invoke`, vedere [algoritmi paralleli](../../parallel/concrt/parallel-algorithms.md).

Per esempi completi che illustrano come usare la classe `join`, vedere [procedura: selezionare tra le attività completate](../../parallel/concrt/how-to-select-among-completed-tasks.md) e [procedura dettagliata: uso di join per impedire il deadlock](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

[[Torna all'inizio](#top)]

## <a name="timer"></a>timer (classe)

La classe Concurrency::[timer](../../parallel/concrt/reference/timer-class.md) funge da origine del messaggio. Un oggetto `timer` Invia un messaggio a una destinazione dopo che è trascorso un periodo di tempo specificato. La classe `timer` è utile quando è necessario ritardare l'invio di un messaggio o si desidera inviare un messaggio a intervalli regolari.

La classe `timer` invia il messaggio a una sola destinazione. Se si imposta il parametro `_PTarget` nel costruttore su `NULL`, è possibile specificare in un secondo momento la destinazione chiamando il metodo [Concurrency:: ISource:: link_target](reference/source-block-class.md#link_target) .

Un oggetto `timer` può essere ripetuto o non ripetuto. Per creare un timer ripetuto, passare **true** per il parametro `_Repeating` quando si chiama il costruttore. In caso contrario, passare **false** per il parametro `_Repeating` per creare un timer non ripetuto. Se il timer si ripete, invia lo stesso messaggio alla destinazione dopo ogni intervallo.

La libreria di agenti crea `timer` oggetti nello stato non avviato. Per avviare un oggetto timer, chiamare il metodo [Concurrency:: timer:: Start](reference/timer-class.md#start) . Per arrestare un oggetto `timer`, eliminare definitivamente l'oggetto o chiamare il metodo [Concurrency:: timer:: Stop](reference/timer-class.md#stop) . Per sospendere un timer ripetuto, chiamare il metodo [Concurrency:: timer::p ause](reference/timer-class.md#pause) .

### <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata la struttura di base di come utilizzare la classe `timer`. Nell'esempio vengono utilizzati `timer` e `call` oggetti per indicare lo stato di un'operazione di lunga durata.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Questo esempio produce l'output di esempio seguente:

```Output
Computing fib(42)..................................................result is 267914296
```

Per un esempio completo in cui viene illustrato come usare la classe `timer`, vedere [procedura: inviare un messaggio a intervalli regolari](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[[Torna all'inizio](#top)]

## <a name="filtering"></a>Filtro messaggi

Quando si crea un oggetto Message Block, è possibile specificare una *funzione di filtro* che determini se il blocco del messaggio accetta o rifiuta un messaggio. Una funzione di filtro è un modo utile per garantire che un blocco di messaggi riceva solo determinati valori.

Nell'esempio seguente viene illustrato come creare un oggetto `unbounded_buffer` che utilizza una funzione di filtro per accettare solo numeri pari. L'oggetto `unbounded_buffer` rifiuta i numeri dispari e pertanto non propaga i numeri dispari nei blocchi di destinazione.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

Nell'esempio viene prodotto l'output seguente:

```Output
0 2 4 6 8
```

Una funzione di filtro può essere una funzione lambda, un puntatore a funzione o un oggetto funzione. Ogni funzione di filtro accetta uno dei formati seguenti.

```Output
bool (T)
bool (T const &)
```

Per eliminare la copia dei dati non necessaria, utilizzare il secondo form quando si dispone di un tipo di aggregazione propagato per valore.

Il filtro dei messaggi supporta il modello di programmazione del *flusso* di dati, in cui i componenti eseguono i calcoli quando ricevono i dati. Per esempi che usano funzioni di filtro per controllare il flusso di dati in un messaggio di rete, vedere [procedura: usare un filtro di blocco dei messaggi](../../parallel/concrt/how-to-use-a-message-block-filter.md), [procedura dettagliata: creazione di un agente del flusso](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)di dati e [procedura dettagliata: creazione](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)di una rete per l'elaborazione di immagini.

[[Torna all'inizio](#top)]

## <a name="reservation"></a>Prenotazione messaggi

La *prenotazione dei messaggi* consente a un blocco di messaggi di riservare un messaggio per un uso successivo. In genere, la prenotazione del messaggio non viene usata direttamente. Tuttavia, la comprensione della prenotazione dei messaggi può essere utile per comprendere meglio il comportamento di alcuni tipi di blocchi di messaggi predefiniti.

Prendere in considerazione join non greedy e greedy. Entrambi utilizzano la prenotazione dei messaggi per riservare i messaggi per un uso successivo. Una descrizione precedente, un join non greedy riceve i messaggi in due fasi. Durante la prima fase, un oggetto `join` non greedy attende che ognuna delle relative origini riceva un messaggio. Un join non greedy tenta quindi di riservare ognuno di questi messaggi. Se può riservare ogni messaggio, utilizzerà tutti i messaggi e li propagherà nella destinazione. In caso contrario, rilascia o Annulla, le prenotazioni dei messaggi e attende di nuovo che ogni origine riceva un messaggio.

Un join greedy, che legge anche i messaggi di input da diverse origini, usa la prenotazione dei messaggi per leggere altri messaggi durante l'attesa di ricevere un messaggio da ogni origine. Si consideri ad esempio un join greedy che riceve messaggi da blocchi di messaggi `A` e `B`. Se il join greedy riceve due messaggi da B ma non ha ancora ricevuto un messaggio da `A`, il join greedy salva l'identificatore univoco del messaggio per il secondo messaggio da `B`. Quando il join greedy riceve un messaggio da `A` e propaga questi messaggi, usa l'identificatore del messaggio salvato per verificare se il secondo messaggio da `B` è ancora disponibile.

È possibile utilizzare la prenotazione dei messaggi quando si implementano tipi di blocchi di messaggi personalizzati. Per un esempio su come creare un tipo di blocco di messaggi personalizzato, vedere [procedura dettagliata: creazione di un blocco di messaggi personalizzato](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[[Torna all'inizio](#top)]

## <a name="see-also"></a>Vedere anche

[Libreria di agenti asincroni](../../parallel/concrt/asynchronous-agents-library.md)
