---
title: Funzioni dello spazio dei nomi concurrency
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 15b265744640628425502706d69fd98a1c64bda2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374377"
---
# <a name="concurrency-namespace-functions"></a>Funzioni dello spazio dei nomi concurrency

||||
|-|-|-|
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing (DisabilitaTracing)](#disabletracing)|
|[EnableTracing (EnableTracing)](#enabletracing)|[Gratuito](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[Asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[Chiaro](#clear)|[Create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[Parallel_for](#parallel_for)|[Parallel_for_each](#parallel_for_each)|
|[Parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[Ricevere](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[send](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[Swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Aspettare](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a><a name="alloc"></a>Alloc

Assegna un blocco di memoria dalle dimensioni specificate dal suballocatore di cache del runtime di concorrenza.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parametri

*_NumBytes*<br/>
Numero di byte di memoria da allocare.

### <a name="return-value"></a>Valore restituito

Puntatore alla memoria appena allocata.

### <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sugli scenari dell'applicazione che potrebbero trarre vantaggio dall'utilizzo del Suballocator di memorizzazione nella cache, vedere [Utilità di pianificazione](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a><a name="asend"></a>Asend

Un'operazione di invio asincrona che pianifica un'attività per propagare i dati nel blocco di destinazione.

```cpp
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Tipo di dati da inviare.

*_Trg*<br/>
Puntatore o riferimento alla destinazione a cui vengono inviati i dati.

*_Data*<br/>
Riferimento ai dati da inviare.

### <a name="return-value"></a>Valore restituito

**true** se il messaggio è stato accettato prima della restituzione del metodo, **false** in caso contrario.

### <a name="remarks"></a>Osservazioni

Per ulteriori informazioni, vedere [Funzioni di passaggio dei messaggi](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a><a name="cancel_current_task"></a>cancel_current_task

Annulla l'attività attualmente in esecuzione. Questa funzione può essere chiamata dal corpo di un'attività per interrompere l'esecuzione dell'attività e forzarne il passaggio allo stato `canceled`.

Chiamare questa funzione non è uno scenario supportato se non si è all'interno del corpo di un oggetto `task`. Questa operazione provocherà un comportamento non definito, ad esempio un arresto anomalo o un blocco nell'applicazione.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a><a name="clear"></a>Chiaro

Cancella la coda simultanea, eliminando tutti gli elementi attualmente accodati. Questo metodo non è indipendente dalla concorrenza.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parametri

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a><a name="create_async"></a>Create_async

Crea un costrutto asincrono di Windows Runtime in base a un'espressione lambda o un oggetto funzione fornito dall'utente. Il tipo restituito `create_async` è uno tra `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` o `IAsyncOperationWithProgress<TResult, TProgress>^` in base alla firma dell'espressione lambda passata al metodo.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parametri

*_Function*<br/>
Digitare 

*_Func*<br/>
Espressione lambda o oggetto funzione da cui si crea un costrutto asincrono di Windows Runtime.

### <a name="return-value"></a>Valore restituito

Un costrutto asincrono rappresentato da un\<IAsyncAction, IAsyncActionWithProgress TProgress>, IAsyncOperation\<TResult>, o un IAsyncOperationWithProgress\<TResult, TProgress>. L'interfaccia restituita dipende dalla firma dell'espressione lambda passata nella funzione.

### <a name="remarks"></a>Osservazioni

Il tipo restituito dell'espressione lambda determina se il costrutto è un'azione o un'operazione.

Le espressioni lambda tramite cui viene restituito void comportano la creazione di azioni. Le espressioni lambda tramite cui viene restituito un risultato di tipo `TResult` comportano la creazione di operazioni TResult.

L'espressione lambda può inoltre restituire `task<TResult>` che incapsula il lavoro asincrono o è la continuazione di una catena di attività che rappresentano il lavoro asincrono. In questo caso, la stessa espressione lambda viene eseguita inline, poiché le attività sono quelle che vengono eseguite in modo asincrono e viene rimosso il wrapping del tipo restituito dell'espressione lambda per generare il costrutto asincrono restituito da `create_async`. Ciò implica che un'espressione lambda che restituisce un'attività void> causerà la creazione di azioni e un'espressione lambda che restituisce un'attività TResult> causerà la creazione di operazioni di TResult.This implies that a lambda that returns a task\<void> will cause the creation of actions, and a lambda that returns a task\<TResult> will cause the creation of operations of TResult.

L'espressione lambda può accettare zero, uno o due argomenti. Gli argomenti validi sono `progress_reporter<TProgress>` e `cancellation_token`, in questo ordine se vengono usati entrambi. Un'espressione lambda senza argomenti determina la creazione di un costrutto asincrono senza la funzionalità per la segnalazione dello stato di avanzamento. Un'espressione lambda\<che accetta un `create_async` progress_reporter TProgress> causerà la restituzione `report` di un costrutto asincrono che segnala lo stato di avanzamento del tipo TProgress ogni volta che viene chiamato il metodo dell'oggetto progress_reporter. Un'espressione lambda che accetta un cancellation_token può usare tale token per verificare l'annullamento oppure passarlo alle attività create in modo che l'annullamento del costrutto asincrono provochi l'annullamento di tali attività.

Se il corpo dell'oggetto lambda o funzione restituisce un risultato (e non un'attività\<TResult>), il lamdba verrà eseguito in modo asincrono all'interno dell'MTA processo nel contesto di un'attività creata in modo implicito dal runtime. Il metodo `IAsyncInfo::Cancel` determina l'annullamento dell'attività implicita.

Se tramite il corpo di lambda viene restituita un'attività, lambda viene eseguito inline e, dichiarando che nel lambda viene accettato un argomento di tipo `cancellation_token`, è possibile attivare l'annullamento delle attività create all'interno di lambda passando il token quando vengono create. È inoltre possibile usare il metodo `register_callback` sul token per fare in modo che il runtime richiami un callback quando si chiama `IAsyncInfo::Cancel` sull'operazione async o sull'azione prodotta.

Questa funzione è disponibile solo per le app di Windows Runtime.

## <a name="createresourcemanager"></a><a name="createresourcemanager"></a>CreateResourceManager

Restituisce un'interfaccia che rappresenta l'istanza singleton di Gestione risorse del runtime di concorrenza. Gestione risorse è responsabile dell'assegnazione di risorse a utilità di pianificazione che vogliono cooperare tra loro.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Valore restituito

Interfaccia `IResourceManager`.

### <a name="remarks"></a>Osservazioni

Più chiamate successive a questo metodo restituiranno la stessa istanza di Gestione risorse. Ogni chiamata al metodo incrementa un conteggio dei riferimenti in Gestione risorse e deve essere abbinata a una chiamata al metodo [IResourceManager::Release](iresourcemanager-structure.md) al termine della comunicazione dell'utilità di pianificazione con Gestione risorse.

[unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal runtime di concorrenza.

## <a name="create_task"></a><a name="create_task"></a>create_task

Crea un oggetto [attività](task-class.md) PPL. `create_task` può essere usato ovunque si sarebbe usato un costruttore di attività. Viene fornito principalmente per comodità, in quanto consente l'uso della parola chiave `auto` durante la creazione delle attività.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Tipo del parametro dal quale deve essere costruita l'attività.

*_ReturnType*<br/>
Digitare 

*_Param*<br/>
Parametro dal quale deve essere costruita l'attività. Può trattarsi di un oggetto `task_completion_event` lambda o `task` di funzione, di un oggetto, di un oggetto diverso o di un'interfaccia Windows::Foundation::IAsyncInfo se si usano attività nell'app UWP.

*_TaskOptions*<br/>
Le opzioni dell'attività.

*_Task*<br/>
Attività da creare.

### <a name="return-value"></a>Valore restituito

Nuova attività di `T`tipo , dedotta da `_Param`.

### <a name="remarks"></a>Osservazioni

Il primo overload si comporta come un costruttore di attività che accetta un singolo parametro.

Il secondo overload associa il token di annullamento fornito all'attività appena creata. Se si utilizza questo overload non è `task` consentito passare un oggetto diverso come primo parametro.

Il tipo dell'attività restituita viene dedotto dal primo parametro alla funzione. Se `_Param` è `task_completion_event<T>`un `task<T>`, un oggetto o `T` un `task<T>`functor che restituisce `task<T>`un tipo o , il tipo dell'attività creata è .

In `_Param` un'app UWP, se è di tipo Windows::Foundation::IAsyncOperation\<T>o\<Windows::Foundation::IAsyncOperationWithProgress T,P>, o un functor che restituisce uno di questi tipi, l'attività creata sarà di tipo `task<T>`. Se `_Param` è di tipo Windows::Foundation::IAsyncAction o Windows::Foundation::IAsyncActionWithProgress\<P>, o un functor che `task<void>`restituisce uno di questi tipi, l'attività creata dirà il tipo .

## <a name="disabletracing"></a><a name="disabletracing"></a>DisableTracing (DisabilitaTracing)

Disabilita la tracciatura nel runtime di concorrenza. Questa funzione è deprecata poiché la traccia ETW non viene registrata per impostazione predefinita.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Valore restituito

Se la traccia `S_OK` è stata disabilitata correttamente, viene restituito. Se la traccia non è stata iniziata in precedenza, viene restituito `E_NOT_STARTED`.

## <a name="enabletracing"></a><a name="enabletracing"></a>EnableTracing (EnableTracing)

Abilita la tracciatura nel runtime di concorrenza. Questa funzione è deprecata poiché la traccia ETW è ora attivata per impostazione predefinita.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Valore restituito

Se la traccia `S_OK` è stata avviata correttamente, viene restituito; in `E_NOT_STARTED` caso contrario, viene restituito.

## <a name="free"></a><a name="free"></a>Gratuito

Rilascia un blocco di memoria precedentemente allocato dal metodo `Alloc` al suballocatore di cache del runtime di concorrenza.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parametri

*_PAllocation*<br/>
Puntatore alla memoria precedentemente allocato dal `Alloc` metodo che deve essere liberato. Se il `_PAllocation` parametro è `NULL`impostato sul valore , questo metodo lo ignorerà e restituirà immediatamente.

### <a name="remarks"></a>Osservazioni

Per ulteriori informazioni sugli scenari dell'applicazione che potrebbero trarre vantaggio dall'utilizzo del Suballocator di memorizzazione nella cache, vedere [Utilità di pianificazione](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a><a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Valore restituito

## <a name="getexecutioncontextid"></a><a name="getexecutioncontextid"></a>GetExecutionContextId

Restituisce un identificatore univoco che può essere assegnato a un contesto di esecuzione che implementa l'interfaccia `IExecutionContext`.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Valore restituito

Identificatore univoco per un contesto di esecuzione.

### <a name="remarks"></a>Osservazioni

Utilizzare questo metodo per ottenere un identificatore `IExecutionContext` per il contesto di esecuzione prima di passare un'interfaccia come parametro a uno dei metodi offerti da Gestione risorse.

## <a name="getosversion"></a><a name="getosversion"></a>GetOSVersion

Restituisce la versione del sistema operativo.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Valore restituito

Valore enumerato che rappresenta il sistema operativo.

### <a name="remarks"></a>Osservazioni

[unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal runtime di concorrenza.

## <a name="getprocessorcount"></a><a name="getprocessorcount"></a>GetProcessorCount

Restituisce il numero dei thread hardware sul sistema sottostante.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Valore restituito

Numero di thread di hardware.

### <a name="remarks"></a>Osservazioni

[unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal runtime di concorrenza.

## <a name="getprocessornodecount"></a><a name="getprocessornodecount"></a>GetProcessorNodeCount

Restituisce il numero di nodi NUMA o pacchetti del processore sul sistema sottostante.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Valore restituito

Numero di nodi NUMA o pacchetti del processore.

### <a name="remarks"></a>Osservazioni

Se il sistema contiene più nodi NUMA rispetto ai pacchetti del processore, viene restituito il numero di nodi NUMA, in caso contrario, viene restituito il numero di pacchetti del processore.

[unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal runtime di concorrenza.

## <a name="getschedulerid"></a><a name="getschedulerid"></a>GetSchedulerId

Restituisce un identificatore univoco che può essere assegnato a un'utilità di pianificazione che implementa l'interfaccia `IScheduler`.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Valore restituito

Identificatore univoco di un'utilità di pianificazione.

### <a name="remarks"></a>Osservazioni

Utilizzare questo metodo per ottenere un identificatore `IScheduler` per l'utilità di pianificazione prima di passare un'interfaccia come parametro a uno dei metodi offerti da Gestione risorse.

## <a name="internal_assign_iterators"></a><a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Parametri

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*Prima*<br/>

*Ultima*<br/>

## <a name="interruption_point"></a><a name="interruption_point"></a>interruption_point

Crea un punto di interruzione per l'annullamento. Se un annullamento è in corso nel contesto in cui questa funzione viene chiamata, questa genererà un'eccezione interna che interrompe l'esecuzione del lavoro parallelo in esecuzione. Se l'annullamento non è in corso, la funzione non esegue alcuna operazione.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Osservazioni

Non è consigliabile rilevare l'eccezione di annullamento interna generata dalla funzione `interruption_point()`. L'eccezione viene rilevata e gestita dal runtime, pertanto se viene rilevata potrebbe comportare un'esecuzione anomala del programma.

## <a name="is_current_task_group_canceling"></a><a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Restituisce un'informazione che indica se il gruppo di attività attualmente in esecuzione inline sul contesto corrente si trova nel mezzo di un annullamento attivo (o lo sarà a breve). Si noti che se non è presente alcun gruppo di attività in esecuzione inline sul contesto corrente, sarà restituito `false`.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Valore restituito

**true** se il gruppo di attività attualmente in esecuzione sta annullando, **false** in caso contrario.

### <a name="remarks"></a>Osservazioni

Per ulteriori informazioni, vedere [Annullamento](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a><a name="make_choice"></a>make_choice

Costruisce un blocco della messaggistica `choice` da un oggetto `Scheduler` o `ScheduleGroup` facoltativo e due o più origini di input.

```cpp
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parametri

*T1*<br/>
Tipo di blocco dei messaggi della prima origine.

*T2*<br/>
Tipo di blocco dei messaggi della seconda origine.

*_PScheduler*<br/>
Oggetto `Scheduler` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `choice` .

*_Item1*<br/>
Prima origine.

*_Item2*<br/>
Seconda origine.

*_Items*<br/>
Origini supplementari.

*_PScheduleGroup*<br/>
Oggetto `ScheduleGroup` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `choice` . L'oggetto `Scheduler` usato è previsto dal gruppo di pianificazione.

### <a name="return-value"></a>Valore restituito

Blocco di messaggi `choice` con due o più origini di input.

## <a name="make_greedy_join"></a><a name="make_greedy_join"></a>make_greedy_join

Costruisce un blocco della messaggistica `greedy multitype_join` da un oggetto `Scheduler` o `ScheduleGroup` facoltativo e due o più origini di input.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>Parametri

*T1*<br/>
Tipo di blocco dei messaggi della prima origine.

*T2*<br/>
Tipo di blocco dei messaggi della seconda origine.

*_PScheduler*<br/>
Oggetto `Scheduler` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` .

*_Item1*<br/>
Prima origine.

*_Item2*<br/>
Seconda origine.

*_Items*<br/>
Origini supplementari.

*_PScheduleGroup*<br/>
Oggetto `ScheduleGroup` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` . L'oggetto `Scheduler` usato è previsto dal gruppo di pianificazione.

### <a name="return-value"></a>Valore restituito

Blocco di messaggi `greedy multitype_join` con due o più origini di input.

## <a name="make_join"></a><a name="make_join"></a>make_join

Costruisce un blocco della messaggistica `non_greedy multitype_join` da un oggetto `Scheduler` o `ScheduleGroup` facoltativo e due o più origini di input.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parametri

*T1*<br/>
Tipo di blocco dei messaggi della prima origine.

*T2*<br/>
Tipo di blocco dei messaggi della seconda origine.

*_PScheduler*<br/>
Oggetto `Scheduler` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` .

*_Item1*<br/>
Prima origine.

*_Item2*<br/>
Seconda origine.

*_Items*<br/>
Origini supplementari.

*_PScheduleGroup*<br/>
Oggetto `ScheduleGroup` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` . L'oggetto `Scheduler` usato è previsto dal gruppo di pianificazione.

### <a name="return-value"></a>Valore restituito

Blocco di messaggi `non_greedy multitype_join` con due o più origini di input.

## <a name="make_task"></a><a name="make_task"></a>make_task

Un metodo factory per la creazione di un oggetto `task_handle`.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parametri

*_Function*<br/>
Tipo dell'oggetto funzione che verrà richiamato per eseguire `task_handle` il lavoro rappresentato dall'oggetto.

*_Func*<br/>
Funzione che verrà richiamata per eseguire il `task_handle` lavoro rappresentato dall'oggetto. Può trattarsi di un funtore lambda, un puntatore a una funzione o qualsiasi `void operator()()`oggetto che supporta una versione dell'operatore di chiamata di funzione con la firma .

### <a name="return-value"></a>Valore restituito

Oggetto `task_handle` .

### <a name="remarks"></a>Osservazioni

Questa funzione è utile quando `task_handle` è necessario creare un oggetto con un'espressione lambda, perché consente di creare l'oggetto senza conoscere il tipo reale del funtore lambda.

## <a name="parallel_buffered_sort"></a><a name="parallel_buffered_sort"></a>parallel_buffered_sort

Dispone gli elementi in un intervallo specificato in un ordine non decrescente o in base a un criterio di ordinamento specificato da un predicato binario, in parallelo. Questa funzione è semanticamente simile a `std::sort` in quanto si tratta di un ordinamento basato sul confronto, instabile, sul posto, ma richiede uno spazio aggiuntivo pari `O(n)` e l'inizializzazione predefinita per gli elementi in fase di ordinamento.

```cpp
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parametri

*_Random_iterator*<br/>
Tipo dell'iteratore dell'intervallo di input.

*_Allocator*<br/>
Il tipo di un allocatore di memoria compatibile con la libreria standard di C.

*_Function*<br/>
Tipo del comparatore binario.

*_Begin*<br/>
Iteratore ad accesso casuale che punta alla posizione del primo elemento nell'intervallo da ordinare.

*_End*<br/>
Iteratore ad accesso casuale che punta alla prima posizione oltre l'elemento finale nell'intervallo da ordinare.

*_Alloc*<br/>
Un'istanza di un allocatore di memoria compatibile con la libreria standard di C.

*_Func*<br/>
Oggetto funzione predicato definito dall'utente tramite cui vengono definiti i criteri di confronto che devono essere soddisfatti dagli elementi successivi nell'ordinamento. Un predicato binario accetta due argomenti e restituisce **true** se la condizione è soddisfatta e **false** se non lo è. Tramite questa funzione di confronto deve essere imposto un ordinamento di tipo "strict weak" alle coppie di elementi della sequenza.

*_Chunk_size*<br/>
Dimensione minima di un blocco che verrà suddiviso in due per l'esecuzione parallela.

### <a name="remarks"></a>Osservazioni

Tutti gli `n * sizeof(T)` overload richiedono `n` spazio aggiuntivo, dove è il `T` numero di elementi da ordinare ed è il tipo di elemento. Nella maggior parte dei casi parallel_buffered_sort mostrerà un miglioramento delle prestazioni rispetto [parallel_sort,](concurrency-namespace-functions.md)ed è consigliabile utilizzarlo su parallel_sort se si dispone della memoria disponibile.

Se non si fornisce un confronto `std::less` binario, come valore predefinito, che richiede `operator<()`che il tipo di elemento fornisca l'operatore .

Se non si specifica un tipo o un'istanza di allocatore, per allocare il buffer viene utilizzato l'allocatore `std::allocator<T>` di memoria della libreria standard di C.

Tramite l'algoritmo l'intervallo di input viene diviso in due blocchi e successivamente ogni blocco viene diviso in due blocchi secondari per l'esecuzione in parallelo. L'argomento `_Chunk_size` facoltativo può essere utilizzato per indicare all'algoritmo che deve gestire blocchi di dimensioni < `_Chunk_size` in modo seriale.

## <a name="parallel_for"></a><a name="parallel_for"></a>Parallel_for

`parallel_for` viene iterato su un intervallo di indici ed esegue una funzione fornita dall'utente a ogni iterazione, in parallelo.

```cpp
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>Parametri

*_Index_type*<br/>
Tipo dell'indice utilizzato per l'iterazione.

*_Function*<br/>
Tipo della funzione che verrà eseguita a ogni iterazione.

*_Partitioner*<br/>
Tipo di partitioner utilizzato per partizionare l'intervallo fornito.

*Prima*<br/>
Primo indice da includere nell'iterazione.

*Ultima*<br/>
Indice 1 dopo l'ultimo indice da includere nell'iterazione.

*_Step*<br/>
Valore in base al quale eseguire `first` `last`l'iterazione durante l'iterazione da a . Il passo deve essere positivo. [invalid_argument](../../../standard-library/invalid-argument-class.md) viene generata una invalid_argument se il passaggio è minore di 1.

*_Func*<br/>
Funzione da eseguire a ogni iterazione. Può trattarsi di un'espressione lambda, di un puntatore a funzione o `void operator()(_Index_type)`di qualsiasi oggetto che supporti una versione dell'operatore di chiamata di funzione con la firma .

*_Part*<br/>
Riferimento all'oggetto partitioner. L'argomento può `const`essere `const`uno di [auto_partitioner](auto-partitioner-class.md)`&`, [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` o [affinity_partitioner](affinity-partitioner-class.md) `&` Se viene utilizzato un oggetto [affinity_partitioner,](affinity-partitioner-class.md) il riferimento deve essere un riferimento l-value non const, in modo che l'algoritmo possa archiviare lo stato per i cicli futuri da riutilizzare.

### <a name="remarks"></a>Osservazioni

Per ulteriori informazioni, vedere [Algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a><a name="parallel_for_each"></a>Parallel_for_each

`parallel_for_each` applica una funzione specificata a ogni elemento all'interno di un intervallo, in parallelo. È semanticamente equivalente alla funzione `for_each` nello spazio dei nomi `std`, fatta eccezione per l'iterazione sugli elementi, che viene eseguita in parallelo, e per l'ordine di iterazione, che non è specificato. L'argomento `_Func` deve supportare un operatore di chiamata della funzione del form `operator()(T)` laddove il parametro `T` è il tipo di elemento del contenitore su cui viene eseguita l'iterazione.

```cpp
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>Parametri

*_Iterator*<br/>
Tipo dell'iteratore utilizzato per scorrere il contenitore.

*_Function*<br/>
Tipo della funzione che verrà applicato a ogni elemento all'interno dell'intervallo.

*_Partitioner*<br/>
*Prima*<br/>
Iteratore che punta alla posizione del primo elemento da includere nell'iterazione parallela.

*Ultima*<br/>
Un iteratore che indirizza la posizione di un passaggio oltre l'elemento finale da includere nell'iterazione parallela.

*_Func*<br/>
Oggetto funzione definito dall'utente applicato a ogni elemento dell'intervallo.

*_Part*<br/>
Riferimento all'oggetto partitioner. L'argomento può `const`essere `const`uno di [auto_partitioner](auto-partitioner-class.md)`&`, [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` o [affinity_partitioner](affinity-partitioner-class.md) `&` Se viene utilizzato un oggetto [affinity_partitioner,](affinity-partitioner-class.md) il riferimento deve essere un riferimento l-value non const, in modo che l'algoritmo possa archiviare lo stato per i cicli futuri da riutilizzare.

### <a name="remarks"></a>Osservazioni

[auto_partitioner](auto-partitioner-class.md) verrà utilizzato per l'overload senza un partitioner esplicito.

Per gli iteratori che non supportano l'accesso casuale, è supportato solo [auto_partitioner.](auto-partitioner-class.md)

Per ulteriori informazioni, vedere [Algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a><a name="parallel_invoke"></a>Parallel_invoke

Esegue gli oggetti funzione forniti come parametri in parallelo e blocca fino al termine dell'esecuzione. Ogni oggetto funzione potrebbe essere un'espressione lambda, un puntatore a funzione o qualsiasi oggetto che supporta l'operatore della chiamata di funzione con la firma `void operator()()`.

```cpp
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>Parametri

*_Function1*<br/>
Tipo del primo oggetto funzione da eseguire in parallelo.

*_Function2*<br/>
Tipo del secondo oggetto funzione da eseguire in parallelo.

*_Function3*<br/>
Tipo del terzo oggetto funzione da eseguire in parallelo.

*_Function4*<br/>
Tipo del quarto oggetto funzione da eseguire in parallelo.

*_Function5*<br/>
Tipo del quinto oggetto funzione da eseguire in parallelo.

*_Function6*<br/>
Tipo del sesto oggetto funzione da eseguire in parallelo.

*_Function7*<br/>
Tipo del settimo oggetto funzione da eseguire in parallelo.

*_Function8*<br/>
Tipo dell'ottavo oggetto funzione da eseguire in parallelo.

*_Function9*<br/>
Tipo del nono oggetto funzione da eseguire in parallelo.

*_Function10*<br/>
Tipo dell'oggetto funzione decicabile da eseguire in parallelo.

*_Func1*<br/>
Primo oggetto funzione da eseguire in parallelo.

*_Func2*<br/>
Secondo oggetto funzione da eseguire in parallelo.

*_Func3*<br/>
Terzo oggetto funzione da eseguire in parallelo.

*_Func4*<br/>
Quarto oggetto funzione da eseguire in parallelo.

*_Func5*<br/>
Quinto oggetto funzione da eseguire in parallelo.

*_Func6*<br/>
Il sesto oggetto funzione da eseguire in parallelo.

*_Func7*<br/>
Settimo oggetto funzione da eseguire in parallelo.

*_Func8*<br/>
L'ottavo oggetto funzione da eseguire in parallelo.

*_Func9*<br/>
Nono viene eseguito in parallelo il nono oggetto funzione.

*_Func10*<br/>
Valore decimo oggetto funzione da eseguire in parallelo.

### <a name="remarks"></a>Osservazioni

Si noti che uno o più oggetti funzione forniti come parametri possono essere eseguiti inline nel contesto di chiamata.

Se uno o più oggetti funzione passati come parametri a questa funzione generaun'eccezione, il runtime selezionerà `parallel_invoke`un'eccezione di questo tipo di scelta e la propagherà dalla chiamata a .

Per ulteriori informazioni, vedere [Algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a><a name="parallel_radixsort"></a>parallel_radixsort

Dispone gli elementi in un intervallo specificato in un ordine non decrescente usando l'algoritmo Radix Sort. Si tratta di una funzione stabile di ordinamento che richiede una funzione di proiezione affinché che consente agli elementi del progetto di essere ordinati nelle chiavi di tipo intero senza segno. L'inizializzazione predefinita è necessaria per gli elementi da ordinare.

```cpp
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>Parametri

*_Random_iterator*<br/>
Tipo dell'iteratore dell'intervallo di input.

*_Allocator*<br/>
Il tipo di un allocatore di memoria compatibile con la libreria standard di C.

*_Function*<br/>
Tipo della funzione di proiezione.

*_Begin*<br/>
Iteratore ad accesso casuale che punta alla posizione del primo elemento nell'intervallo da ordinare.

*_End*<br/>
Iteratore ad accesso casuale che punta alla prima posizione oltre l'elemento finale nell'intervallo da ordinare.

*_Alloc*<br/>
Un'istanza di un allocatore di memoria compatibile con la libreria standard di C.

*_Proj_func*<br/>
Oggetto funzione di proiezione definito dall'utente che converte un elemento in un valore integrale.

*_Chunk_size*<br/>
Dimensione minima di un blocco che verrà suddiviso in due per l'esecuzione parallela.

### <a name="remarks"></a>Osservazioni

Tutti gli `n * sizeof(T)` overload richiedono `n` spazio aggiuntivo, dove è il `T` numero di elementi da ordinare ed è il tipo di elemento. Un funtore di proiezione unario con la firma `I _Proj_func(T)` è `T` necessario restituire `I` una chiave quando viene fornito un elemento, dove è il tipo di elemento ed è un tipo integer senza segno.

Se non si fornisce una funzione di proiezione, una funzione di proiezione predefinita che restituisce semplicemente l'elemento viene utilizzata per i tipi integrali. La funzione non verrà compilata se l'elemento non è un tipo integrale in assenza di una funzione di proiezione.

Se non si specifica un tipo o un'istanza di allocatore, per allocare il buffer viene utilizzato l'allocatore `std::allocator<T>` di memoria della libreria standard di C.

Tramite l'algoritmo l'intervallo di input viene diviso in due blocchi e successivamente ogni blocco viene diviso in due blocchi secondari per l'esecuzione in parallelo. L'argomento `_Chunk_size` facoltativo può essere utilizzato per indicare all'algoritmo che deve gestire blocchi di dimensioni < `_Chunk_size` in modo seriale.

## <a name="parallel_reduce"></a><a name="parallel_reduce"></a>parallel_reduce

Calcola la somma di tutti gli elementi in un intervallo specificato elaborando le somme parziali successive, o calcola il risultato dei risultati parziali successivi ottenuti analogamente tramite l'uso di un'operazione binaria specificata diversa da quella di somma, in parallelo. `parallel_reduce` è semanticamente simile a `std::accumulate`, con la differenza che richiede all'operazione binaria di essere associativa e richiede un valore di identità anziché un valore iniziale.

```cpp
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>Parametri

*_Forward_iterator*<br/>
Tipo di iteratore dell'intervallo di input.

*_Sym_reduce_fun*<br/>
Tipo della funzione di riduzione simmetrica. Deve essere un tipo `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`di funzione con firma , dove _Reduce_type è uguale al tipo di identità e al tipo di risultato della riduzione. Per il terzo overload, questo deve essere `_Range_reduce_fun`coerente con il tipo di output di .

*_Reduce_type*<br/>
Tipo in cui verrà ridotto l'input, che può essere diverso dal tipo di elemento di input. Il valore restituito e il valore Identity avranno questo tipo.

*_Range_reduce_fun*<br/>
Tipo della funzione di riduzione dell'intervallo. Deve essere un tipo `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`di funzione con firma , _Reduce_type è uguale al tipo di identità e al tipo di risultato della riduzione.

*_Begin*<br/>
Un iteratore di input che punta al primo elemento nell'intervallo da ridurre.

*_End*<br/>
Un iteratore di input che punta all'elemento che è una posizione oltre l'elemento finale nell'intervallo da ridurre.

*_Identity*<br/>
Il valore `_Identity` Identity è dello stesso tipo del tipo `value_type` di risultato della riduzione e anche dell'iteratore per il primo e il secondo overload. Per il terzo overload, il valore Identity deve avere lo stesso tipo del `value_type` tipo di risultato della riduzione, ma può essere diverso da quello dell'iteratore. Deve avere un valore appropriato in `_Range_fun`modo che l'operatore di riduzione dell'intervallo , se applicato a un intervallo di un singolo elemento di tipo `value_type` e il valore Identity, si comporti come un cast di tipo del valore dal tipo `value_type` al tipo identity.

*_Sym_fun*<br/>
La funzione simmetrica che verrà utilizzata nella seconda della riduzione. Fare riferimento a Osservazioni per ulteriori informazioni.

*_Range_fun*<br/>
La funzione che verrà utilizzata nella prima fase della riduzione. Fare riferimento a Osservazioni per ulteriori informazioni.

### <a name="return-value"></a>Valore restituito

Risultato della riduzione.

### <a name="remarks"></a>Osservazioni

Per eseguire una riduzione parallela, la funzione divide l'intervallo in blocchi in base al numero di lavoratori disponibili per l'utilità di pianificazione sottostante. La riduzione avviene in due fasi, la prima fase esegue una riduzione all'interno di ogni blocco e la seconda fase esegue una riduzione tra i risultati parziali di ogni blocco.

Il primo overload richiede che `value_type` `T`l'iteratore di , , sia uguale al tipo di valore Identity e al tipo di risultato di riduzione. Il tipo di elemento `T T::operator + (T)` T deve fornire l'operatore per ridurre gli elementi in ogni blocco. Lo stesso operatore viene utilizzato anche nella seconda fase.

Il secondo overload richiede inoltre `value_type` che l'iteratore sia uguale al tipo di valore Identity e al tipo di risultato di riduzione. L'operatore `_Sym_fun` binario fornito viene utilizzato in entrambe le fasi di riduzione, con il valore Identity come valore iniziale per la prima fase.

Per il terzo overload, il tipo di valore Identity deve essere uguale al tipo di risultato di riduzione, ma l'iteratore `value_type` può essere diverso da entrambi. La funzione `_Range_fun` di riduzione dell'intervallo viene utilizzata nella prima fase `_Sym_reduce_fun` con il valore Identity come valore iniziale e la funzione binaria viene applicata ai risultati secondari nella seconda fase.

## <a name="parallel_sort"></a><a name="parallel_sort"></a>parallel_sort

Dispone gli elementi in un intervallo specificato in un ordine non decrescente o in base a un criterio di ordinamento specificato da un predicato binario, in parallelo. Questa funzione è semanticamente simile a `std::sort` in quanto si tratta di un ordinamento basato sul confronto, instabile, sul posto.

```cpp
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parametri

*_Random_iterator*<br/>
Tipo dell'iteratore dell'intervallo di input.

*_Function*<br/>
Tipo del funtore di confronto binario.

*_Begin*<br/>
Iteratore ad accesso casuale che punta alla posizione del primo elemento nell'intervallo da ordinare.

*_End*<br/>
Iteratore ad accesso casuale che punta alla prima posizione oltre l'elemento finale nell'intervallo da ordinare.

*_Func*<br/>
Oggetto funzione predicato definito dall'utente tramite cui vengono definiti i criteri di confronto che devono essere soddisfatti dagli elementi successivi nell'ordinamento. Un predicato binario accetta due argomenti e restituisce **true** se la condizione è soddisfatta e **false** se non lo è. Tramite questa funzione di confronto deve essere imposto un ordinamento di tipo "strict weak" alle coppie di elementi della sequenza.

*_Chunk_size*<br/>
Dimensione minima di un blocco che verrà suddiviso in due per l'esecuzione parallela.

### <a name="remarks"></a>Osservazioni

Il primo overload utilizza il `std::less`confronto binario .

Nel secondo overload viene utilizzato il confronto binario fornito in cui deve essere presente la firma `bool _Func(T, T)` dove `T` è il tipo degli elementi dell'intervallo di input.

Tramite l'algoritmo l'intervallo di input viene diviso in due blocchi e successivamente ogni blocco viene diviso in due blocchi secondari per l'esecuzione in parallelo. L'argomento `_Chunk_size` facoltativo può essere utilizzato per indicare all'algoritmo che deve gestire blocchi di dimensioni < `_Chunk_size` in modo seriale.

## <a name="parallel_transform"></a><a name="parallel_transform"></a>parallel_transform

Applica un oggetto funzione specificato ad ogni elemento di un intervallo di origine o a una coppia di elementi di due intervalli di origine e copia i valori restituiti dell'oggetto funzione in un intervallo di destinazione, in parallelo. Questa funzione è semanticamente equivalente a `std::transform`.

```cpp
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>Parametri

*_Input_iterator1*<br/>
Tipo del primo iteratore o di quello solo di input.

*_Output_iterator*<br/>
Tipo dell'iteratore di output.

*_Unary_operator*<br/>
Tipo del funtore unario che deve essere eseguito in ogni elemento nell'intervallo di input.

*_Input_iterator2*<br/>
Tipo del secondo iteratore di input.

*_Binary_operator*<br/>
Tipo del funtore binario eseguito a livello pairwise negli elementi di due intervalli di origine.

*_Partitioner*<br/>
*primo 1*<br/>
Iteratore di input che punta alla posizione del primo elemento nel primo intervallo o in quello solo origine da utilizzare.

*ultimo1*<br/>
Iteratore di input che punta alla prima posizione dopo l'elemento finale nel primo intervallo o in quello solo di origine da utilizzare.

*_Result*<br/>
Iteratore di output che punta alla posizione del primo elemento nell'intervallo di destinazione.

*_Unary_op*<br/>
Oggetto funzione unario definito dall'utente che viene applicato a ogni elemento nell'intervallo di origine.

*_Part*<br/>
Riferimento all'oggetto partitioner. L'argomento può `const`essere `const`uno di [auto_partitioner](auto-partitioner-class.md)`&`, [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` o [affinity_partitioner](affinity-partitioner-class.md) `&` Se viene utilizzato un oggetto [affinity_partitioner,](affinity-partitioner-class.md) il riferimento deve essere un riferimento l-value non const, in modo che l'algoritmo possa archiviare lo stato per i cicli futuri da riutilizzare.

*primo 2*<br/>
Iteratore di input che punta alla posizione del primo elemento nel secondo intervallo di origine da utilizzare.

*_Binary_op*<br/>
Oggetto funzione binario definito dall'utente applicato a livello pairwise, in ordine progressivo, ai due intervalli di origine.

### <a name="return-value"></a>Valore restituito

Iteratore di output che punta alla prima posizione dopo l'elemento finale nell'intervallo di destinazione in cui vengono ricevuti gli elementi di output trasformati dall'oggetto funzione.

### <a name="remarks"></a>Osservazioni

[auto_partitioner](auto-partitioner-class.md) verrà utilizzato per gli overload senza un argomento partitioner esplicito.

Per gli iteratori che non supportano l'accesso casuale, è supportato solo [auto_partitioner.](auto-partitioner-class.md)

Tramite gli overload che accettano l'argomento `_Unary_op` l'intervallo di input viene trasformato in quello di output applicando il funtore unario a ogni elemento nell'intervallo di input. `_Unary_op` deve supportare l'operatore di chiamata di funzione con la firma `operator()(T)` dove `T` è il tipo di valore dell'intervallo che viene scorso.

Tramite gli overload che accettano l'argomento `_Binary_op` i due intervalli di input vengono trasformati nell'intervallo di output applicando il funtore binario a un elemento del primo intervallo di input e a un elemento dal secondo. `_Binary_op` deve supportare l'operatore di chiamata di funzione con la firma `operator()(T, U)` dove `T` e `U` sono i tipi di valori dei due iteratori di input.

Per ulteriori informazioni, vedere [Algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a><a name="receive"></a>Ricevere

Un'implementazione di ricezione generale, che consente a un contesto di attendere i dati esattamente da un'origine e di filtrare i valori accettati.

```cpp
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Tipo di payload.

*_Src*<br/>
Puntatore o riferimento all'origine da cui sono previsti i dati.

*_Timeout*<br/>
Tempo massimo per il quale il metodo deve per i dati, in millisecondi.

*_Filter_proc*<br/>
Funzione di filtro che determina se i messaggi devono essere accettati.

### <a name="return-value"></a>Valore restituito

Un valore dall'origine, del tipo di payload.

### <a name="remarks"></a>Osservazioni

Se il `_Timeout` parametro ha un `COOPERATIVE_TIMEOUT_INFINITE`valore diverso dalla costante , viene generata l'eccezione [operation_timed_out](operation-timed-out-class.md) se il periodo di tempo specificato scade prima che venga ricevuto un messaggio. Se si desidera un timeout di lunghezza zero, è necessario `receive` utilizzare la `0` funzione [try_receive,](concurrency-namespace-functions.md) anziché chiamare con un timeout pari a (zero), in quanto è più efficiente e non genera eccezioni sui timeout.

Per ulteriori informazioni, vedere [Funzioni di passaggio dei messaggi](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a><a name="run_with_cancellation_token"></a>run_with_cancellation_token

Esegue un oggetto funzione immediatamente e in modo sincrono nel contesto di uno specifico token di annullamento.

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Parametri

*_Function*<br/>
Tipo dell'oggetto funzione che sarà richiamato.

*_Func*<br/>
Oggetto funzione che verrà eseguito. Questo oggetto deve supportare l'operatore di chiamata di funzione con una firma void(void).

*_Ct*<br/>
Token di annullamento tramite cui verrà controllato l'annullamento implicito dell'oggetto funzione. Utilizzare `cancellation_token::none()` se si desidera che la funzione venga eseguita senza alcuna possibilità di annullamento implicito da un gruppo di attività padre che viene annullato.

### <a name="remarks"></a>Osservazioni

Quando l'oggetto `cancellation_token` viene annullato, verranno attivati tutti i punti di interruzione nell'oggetto funzione. Tramite il token esplicito `_Ct` questo parametro `_Func` verrà isolato dall'annullamento padre se al padre è associato un token diverso o se non ne dispone.

## <a name="send"></a><a name="send"></a>Invia

Un'operazione di invio sincrona che attende fino a quando la destinazione accetta o rifiuta il messaggio.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Tipo di payload.

*_Trg*<br/>
Puntatore o riferimento alla destinazione a cui vengono inviati i dati.

*_Data*<br/>
Riferimento ai dati da inviare.

### <a name="return-value"></a>Valore restituito

**true** se il messaggio è stato accettato, **false** in caso contrario.

### <a name="remarks"></a>Osservazioni

Per ulteriori informazioni, vedere [Funzioni di passaggio dei messaggi](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a><a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parametri

*_Scheduler*<br/>
L'utilità di pianificazione di ambiente da impostare.

## <a name="set_task_execution_resources"></a><a name="set_task_execution_resources"></a>set_task_execution_resources

Limita le risorse di esecuzione usate dai thread di lavoro interni del runtime di concorrenza al set di affinità specificato.

È valido chiamare questo metodo solo prima della creazione di Gestione risorse o tra due cicli di vita di Gestione risorse. Può essere chiamato più volte a condizione che Gestione risorse non esista al momento della chiamata. Dopo aver impostato un limite di affinità, rimane attiva fino alla successiva chiamata al metodo `set_task_execution_resources`.

La maschera di affinità fornita non deve essere un sottoinsieme della maschera di affinità del processo. L'affinità del processo verrà aggiornata, se necessario.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parametri

*_ProcessAffinityMask*<br/>
Maschera di affinità in base alla quale devono essere limitati i thread di lavoro del runtime di concorrenza. Utilizzare questo metodo in un sistema con più di 64 thread hardware solo se si desidera limitare il runtime di concorrenza a un subset del gruppo di processori correnti. In genere, è necessario utilizzare la versione del metodo che accetta una matrice di affinità di gruppo come parametro, per limitare l'affinità in computer con più di 64 thread hardware.

*count*<br/>
Numero di voci `GROUP_AFFINITY` nella matrice specificata dal parametro `_PGroupAffinity`.

*_PGroupAffinity*<br/>
Matrice di voci `GROUP_AFFINITY`.

### <a name="remarks"></a>Osservazioni

Il metodo genererà un'eccezione [invalid_operation](invalid-operation-class.md) se un Gestore risorse è presente al momento della chiamata e un'eccezione [invalid_argument](../../../standard-library/invalid-argument-class.md) se l'affinità specificata genera un set vuoto di risorse.

La versione del metodo che accetta una matrice di affinità di gruppo come parametro deve essere utilizzata solo nei sistemi operativi con versione Windows 7 o superiore. In caso contrario, viene generata un'eccezione [di invalid_operation.](invalid-operation-class.md)

La modifica a livello di codice dell'affinità di processo dopo che questo metodo è stato richiamato non causerà la rivalutazione dell'affinità a cui è limitato da Gestione risorse. Pertanto, tutte le modifiche all'affinità di processo devono essere realizzate prima di chiamare questo metodo.

## <a name="swap"></a><a name="swap"></a>Swap

Scambia gli elementi di due oggetti `concurrent_vector`.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Tipo di dati degli elementi archiviati nei vettori simultanei.

*_Ax*<br/>
Tipo di allocatore dei vettori simultanei.

*_A*<br/>
Vettore simultaneo i cui elementi devono essere scambiati con quelli del vettore `_B`simultaneo.

*_B*<br/>
Vettore simultaneo che fornisce gli elementi da scambiare o il vettore i cui `_A`elementi devono essere scambiati con quelli del vettore simultaneo.

### <a name="remarks"></a>Osservazioni

La funzione di modello è un `concurrent_vector` algoritmo specializzato nella classe contenitore per eseguire la funzione `_A`membro . [concurrent_vector::swap](concurrent-vector-class.md#swap) `_B`( ). Si tratta di istanze di ordinamento parziale dei modelli di funzione da parte del compilatore. Quando le funzioni modello sono sottoposte a overload in modo tale che la corrispondenza del modello con la chiamata di funzione non è univoca, il compilatore seleziona la versione più specializzata della funzione modello. La versione generale della `template <class T> void swap(T&, T&)`funzione template, , nella classe di algoritmi funziona per assegnazione ed è un'operazione lenta. La versione specializzata presente in ogni contenitore è molto più veloce, dal momento che funziona con la rappresentazione interna della classe contenitore.

Questo metodo non è indipendente dalla concorrenza. È necessario assicurarsi che nessun altro thread stia eseguendo operazioni su uno dei vettori simultanei quando si chiama questo metodo.

## <a name="task_from_exception"></a><a name="task_from_exception"></a>task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parametri

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Valore restituito

## <a name="task_from_result"></a><a name="task_from_result"></a>task_from_result

```cpp
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parametri

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Valore restituito

## <a name="trace_agents_register_name"></a><a name="trace_agents_register_name"></a>Trace_agents_register_name

Associa il nome specificato con il blocco di messaggi o l'agente nella traccia ETW.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Tipo dell'oggetto. Si tratta in genere di un blocco di messaggi o di un agente.

*_PObject*<br/>
Puntatore al blocco di messaggi o all'agente che viene denominato nella traccia.

*_Name*<br/>
Nome dell'oggetto fornito.

## <a name="try_receive"></a><a name="try_receive"></a>try_receive

Un'implementazione di ricezione try generale, che consente a un contesto di cercare i dati esattamente da un'origine e di filtrare i valori accettati. Se i dati non sono pronti, il metodo restituirà **false**.

```cpp
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Il tipo di payload

*_Src*<br/>
Puntatore o riferimento all'origine da cui sono previsti i dati.

*_value*<br/>
Un riferimento a una posizione in cui verrà posizionato il risultato.

*_Filter_proc*<br/>
Funzione di filtro che determina se i messaggi devono essere accettati.

### <a name="return-value"></a>Valore restituito

Valore `bool` che indica se un payload `_value`è stato inserito o meno in .

### <a name="remarks"></a>Osservazioni

Per ulteriori informazioni, vedere [Funzioni di passaggio dei messaggi](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a><a name="wait"></a>Aspettare

Consente di sospendere il contesto corrente per un intervallo di tempo specificato.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parametri

*_Milliseconds*<br/>
Numero di millisecondi durante i quali il contesto corrente deve essere sospeso. Se il parametro `_Milliseconds` viene impostato sul valore `0`, il contesto corrente deve essere eseguito in altri contesti eseguibili prima di continuare.

### <a name="remarks"></a>Osservazioni

Se questo metodo viene chiamato su un contesto dell'utilità di pianificazione del runtime di concorrenza, l'utilità di pianificazione troverà un contesto diverso da eseguire nella risorsa sottostante. Poiché l'utilità di pianificazione è cooperativa di natura, non è possibile riprendere il contesto subito dopo il numero di millisecondi specificati. Se tramite l'utilità di pianificazione vengono eseguite altre attività che non vengono passate in modo cooperativo all'utilità, il periodo di attesa potrebbe essere indefinito.

## <a name="when_all"></a><a name="when_all"></a>when_all

Crea un'attività che verrà completata correttamente quando tutte le attività fornite come argomenti verranno completate.

```cpp
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>Parametri

*_Iterator*<br/>
Tipo di iteratore di input.

*_Begin*<br/>
Posizione del primo elemento nell'intervallo di elementi da combinare nell'attività risultante.

*_End*<br/>
Posizione del primo elemento oltre l'intervallo di elementi da combinare nell'attività risultante.

*_TaskOptions*<br/>
Oggetto `task_options`.

### <a name="return-value"></a>Valore restituito

Attività che viene completata correttamente quando tutte le attività di input sono state completate correttamente. Se le attività di input sono di tipo `T`, l'output di questa funzione sarà `task<std::vector<T>>`. Se le attività di input sono di tipo `void`, anche l'attività di output sarà `task<void>`.

### <a name="remarks"></a>Osservazioni

`when_all` è una funzione non bloccante che produce `task` come risultato. A differenza [di task::wait](task-class.md#wait), è sicuro chiamare questa funzione in un'app UWP sul thread ASTA (Application STA).

Se una delle attività viene annullata o genera un'eccezione, l'attività restituita verrà completata in anticipo, nello stato annullato e l'eccezione, se si verifica, verrà generata se si chiama [task::get](task-class.md#get) o `task::wait` su tale attività.

Per ulteriori informazioni, vedere [Parallelismo delle attività](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a><a name="when_any"></a>when_any

Crea un'attività che verrà completata correttamente quando una qualsiasi delle attività fornite come argomenti verrà completata.

```cpp
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>Parametri

*_Iterator*<br/>
Tipo di iteratore di input.

*_Begin*<br/>
Posizione del primo elemento nell'intervallo di elementi da combinare nell'attività risultante.

*_End*<br/>
Posizione del primo elemento oltre l'intervallo di elementi da combinare nell'attività risultante.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token di annullamento che controlla l'annullamento dell'attività restituita. Se non si fornisce un token di annullamento, l'attività risultante riceverà il token di annullamento dell'attività che ne causa il completamento.

### <a name="return-value"></a>Valore restituito

Attività che viene completata correttamente quando una delle attività di input è stata completata. Se le attività di input sono di tipo `T`, l'output di questa funzione sarà un `task<std::pair<T, size_t>>>`, dove il primo elemento della coppia è il risultato dell'attività in corso di completamento e il secondo elemento è l'indice dell'attività completata. Se le attività di input sono di tipo `void` l'output è un `task<size_t>`, dove il risultato è l'indice dell'attività in corso di completamento.

### <a name="remarks"></a>Osservazioni

`when_any` è una funzione non bloccante che produce `task` come risultato. A differenza [di task::wait](task-class.md#wait), è sicuro chiamare questa funzione in un'app UWP sul thread ASTA (Application STA).

Per ulteriori informazioni, vedere [Parallelismo delle attività](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi concurrency](concurrency-namespace.md)
