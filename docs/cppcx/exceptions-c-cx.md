---
title: Eccezioni (C++/CX)
ms.date: 07/02/2019
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
ms.openlocfilehash: ade406dc5db6022978f83715555c425caef4375b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740180"
---
# <a name="exceptions-ccx"></a>Eccezioni (C++/CX)

La gestione degli C++errori in/CX è basata sulle eccezioni. Al livello più fondamentale, i componenti Windows Runtime segnalano gli errori come valori HRESULT. In C++/CX questi valori vengono convertiti in eccezioni fortemente tipizzate che contengono un valore HRESULT e una descrizione della stringa a cui è possibile accedere a livello di codice.  Le eccezioni vengono implementate come oggetto `ref class` che deriva da `Platform::Exception`.  Lo spazio dei nomi `Platform` definisce le classi distinte di eccezioni per i valori HRESULT più comuni; tutti gli altri valori sono segnalati tramite la classe `Platform::COMException` . Tutte le classi di eccezioni presentano un campo [Exception::HResult](platform-exception-class.md#hresult) che puoi utilizzare per recuperare il valore HRESULT originale. È anche possibile esaminare le informazioni sullo stack di chiamate per il codice utente nel debugger che consentono di individuare l'origine dell'eccezione, anche se ha avuto origine nel codice scritto in un linguaggio diverso da C++.

## <a name="exceptions"></a>Eccezioni

Nel C++ programma è possibile generare e intercettare un'eccezione che deriva da un'operazione di Windows Runtime, un'eccezione derivata da `std::exception`o un tipo definito dall'utente. È necessario generare un'eccezione di Windows Runtime solo quando si supera il limite dell'ABI (Application Binary Interface), ad esempio quando il codice che intercetta l'eccezione è scritto in JavaScript. Quando un'eccezione non Windows Runtime C++ raggiunge il limite ABI, l'eccezione viene convertita in un' `Platform::FailureException` eccezione, che rappresenta un valore HRESULT E_FAIL. Per ulteriori informazioni su ABI, vedi [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

È possibile dichiarare un' [eccezione Platform:: Exception](platform-exception-class.md) usando uno di due costruttori che accettano un parametro HRESULT o un parametro HRESULT e un parametro [Platform:: String](platform-string-class.md)^ che può essere passato attraverso l'interfaccia ABI a qualsiasi app Windows Runtime che lo gestisce. In alternativa, puoi dichiarare un'eccezione usando uno di due overload del metodo [Exception::CreateException](platform-exception-class.md#createexception) che accettano un parametro HRESULT o un parametro HRESULT e un parametro `Platform::String^` .

## <a name="standard-exceptions"></a>Eccezioni standard

C++/CX supporta un set di eccezioni standard che rappresentano errori HRESULT tipici. Ogni eccezione standard deriva da [Platform::COMException](platform-comexception-class.md), che a sua volta deriva da `Platform::Exception`. Quando generi un'eccezione che supera il limite dell'ABI, l'eccezione deve essere di tipo standard.

Non puoi derivare un tipo di eccezione personale da `Platform::Exception`. Per generare un'eccezione personalizzata, utilizza un valore HRESULT definito dall'utente per creare un oggetto `COMException` .

Nella tabella seguente sono elencate le eccezioni standard.

|NOME|HRESULT sottostante|Descrizione|
|----------|------------------------|-----------------|
|COMException|*HRESULT definito dall'utente*|Generata quando viene restituito un HRESULT non riconosciuto da una chiamata a un metodo COM.|
|AccessDeniedException|E\_ACCESSDENIED|Generata quando viene negato l'accesso a una risorsa o a una funzionalità.|
|ChangedStateException|E\_STATO\_MODIFICATO|Generata quando i metodi di un iteratore di raccolta o di una visualizzazione di raccolta vengono chiamati dopo che la raccolta padre è stata modificata, invalidando così i risultati del metodo.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Generata quando una classe COM non è stata registrata.|
|DisconnectedException|RPC\_E\_DISCONNESSA|Generata quando un oggetto viene disconnesso dai relativi client.|
|FailureException|E\_NON RIESCONO|Generata quando un'operazione non viene completata correttamente.|
|InvalidArgumentException|E\_INVALIDARG|Generata quando uno degli argomenti forniti a un metodo non è valido.|
|InvalidCastException|E\_NOINTERFACE|Generata quando non è possibile eseguire il cast di un tipo a un altro tipo.|
|NotImplementedException|E\_NOTIMPL|Generata se un metodo di interfaccia non è stato implementato in una classe.|
|NullReferenceException|PUNTATORE\_E|Generata quando viene effettuato un tentativo di dereferenziare un riferimento di oggetto null.|
|ObjectDisposedException|RO\_E\_CHIUSO|Generata quando viene eseguita un'operazione su un oggetto eliminato.|
|OperationCanceledException|INTERROMPI E\_|Generata quando un'operazione viene interrotta.|
|OutOfBoundsException|LIMITI\_E|Generata quando un'operazione tenta di accedere a dati memorizzati al di fuori dell'intervallo valido.|
|OutOfMemoryException|E\_OUTOFMEMORY|Generata quando la memoria disponibile non è sufficiente per completare l'operazione.|
|WrongThreadException|THREAD\_RPC\_EERRATO\_|Generata quando un thread esegue una chiamata tramite un puntatore a interfaccia che è per un oggetto proxy che non appartiene all'apartment del thread.|

## <a name="hresult-and-message-properties"></a>Proprietà Message e HResult

Tutte le eccezioni presentano una proprietà [HResult](platform-comexception-class.md#hresult) e una proprietà [Message](platform-comexception-class.md#message) . La proprietà [Exception::HResult](platform-exception-class.md#hresult) ottiene il valore HRESULT numerico sottostante dell'eccezione. La proprietà [Exception::Message](platform-exception-class.md#message) ottiene la stringa fornita dal sistema che descrive l'eccezione. In Windows 8 il messaggio è disponibile solo nel debugger ed è di sola lettura. Ciò significa che non puoi modificarlo quando generi di nuovo l'eccezione. In Windows 8.1 puoi accedere alla stringa di messaggio a livello di codice e fornire un nuovo messaggio se generi di nuovo l'eccezione. Migliori informazioni sullo stack di chiamate sono inoltre disponibili nel debugger, inclusi gli stack di chiamate per le chiamate asincrone.

### <a name="examples"></a>Esempi

Questo esempio illustra come generare un'eccezione Windows Runtime per le operazioni sincrone:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

Nell'esempio riportato di seguito viene illustrato come intercettare l'eccezione.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Per intercettare le eccezioni generate durante un'operazione asincrona, usare la classe di attività e aggiungere una continuazione di gestione degli errori. La continuazione di gestione degli errori effettua il marshalling delle eccezioni generate in altri thread nel thread chiamante affinché tu possa gestire tutte le potenziali eccezioni da un unico punto nel codice. Per altre informazioni, vedere [Programmazione asincrona in C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Evento UnhandledErrorDetected

In Windows 8.1 è possibile sottoscrivere l'evento statico [Windows:: ApplicationModel:: Core:: CoreApplication:: UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror.unhandlederrordetected) , che fornisce l'accesso agli errori non gestiti che stanno per arrestare il processo. Indipendentemente dall'origine, l'errore raggiunge il gestore come oggetto [Windows::ApplicationModel::Core::UnhandledError](/uwp/api/windows.applicationmodel.core.unhandlederror) passato con gli argomenti dell'evento. Quando chiami `Propagate` sull'oggetto, crea e genera un'eccezione `Platform::*Exception` del tipo corrispondente al codice di errore. Nei blocchi catch puoi salvare lo stato utente, se necessario, quindi consentire il termine del processo chiamando `throw`oppure ripristinare uno stato noto del programma. 'esempio seguente mostra il modello di base:

In app. XAML. h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

In app. XAML. cpp:

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
    try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }
}
```

### <a name="remarks"></a>Note

C++/CX non usa la `finally` clausola.

## <a name="see-also"></a>Vedere anche

[Riferimenti al linguaggio C++/CX](visual-c-language-reference-c-cx.md)<br/>
[Riferimenti a spazi dei nomi](namespaces-reference-c-cx.md)
