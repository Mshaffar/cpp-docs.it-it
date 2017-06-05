---
title: funzioni dello spazio dei nomi Concurrency | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 4a01f48a7d087281ab1e9222d1077e92ab8b0d6c
ms.openlocfilehash: 179913d9a7f0b39349b6a6c85fb03837c98041bc
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-functions"></a>funzioni dello spazio dei nomi Concurrency
||||  
|-|-|-|  
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|  
|[EnableTracing](#enabletracing)|[Gratuito](#free)|[GetExecutionContextId](#getexecutioncontextid)|  
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|  
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|  
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|  
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|  
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|  
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|  
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|  
|[Parallel. Invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|  
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[ricezione](#receive)|  
|[run_with_cancellation_token](#run_with_cancellation_token)|[Invia](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|  
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|  
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[attesa](#wait)|  
|[when_all](#when_all)|[when_any](#when_any)|  
  
##  <a name="alloc"></a>Alloc  
 Assegna un blocco di memoria dalle dimensioni specificate dal suballocatore di cache del runtime di concorrenza.  
  
```
void* __cdecl Alloc(size_t _NumBytes);
```  
  
### <a name="parameters"></a>Parametri  
 `_NumBytes`  
 Il numero di byte di memoria da allocare.  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore alla memoria appena allocata.  
  
### <a name="remarks"></a>Note  
 Per ulteriori informazioni su quali scenari dell'applicazione possono trarre vantaggio dal suballocatore di cache, vedere [utilità di pianificazione](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="asend"></a>asend  
 Un'operazione di invio asincrona che pianifica un'attività per propagare i dati nel blocco di destinazione.  
  
```
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
 `T`  
 Il tipo di dati da inviare.  
  
 `_Trg`  
 Un puntatore o un riferimento alla destinazione a cui i dati vengono inviati.  
  
 `_Data`  
 Riferimento ai dati da inviare.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il messaggio è stato accettato prima della restituzione del metodo `false` in caso contrario.  
  
### <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="cancel_current_task"></a>cancel_current_task  
 Annulla l'attività attualmente in esecuzione. Questa funzione può essere chiamata dal corpo di un'attività per interrompere l'esecuzione dell'attività e forzarne il passaggio allo stato `canceled`.  
  
 Chiamare questa funzione non è uno scenario supportato se non si è all'interno del corpo di un oggetto `task`. Questa operazione provocherà un comportamento non definito, ad esempio un arresto anomalo o un blocco nell'applicazione.  
  
```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```  
  
##  <a name="clear"></a>deselezionare  
 Cancella la coda simultanea, distruggendo qualsiasi elemento attualmente in coda. Questo metodo non è indipendente dalla concorrenza.  
  
```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```   
  
### <a name="parameters"></a>Parametri  
 `T`  
 `_Ax`  
  
##  <a name="create_async"></a>create_async  
 Crea un costrutto asincrono di Windows Runtime in base a un'espressione lambda o un oggetto funzione fornito dall'utente. Il tipo restituito `create_async` è uno tra `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^` o `IAsyncOperationWithProgress<TResult, TProgress>^` in base alla firma dell'espressione lambda passata al metodo.  
  
```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```  
  
### <a name="parameters"></a>Parametri  
 `_Function`  
 `_Func`  
 Espressione lambda o oggetto funzione da cui si crea un costrutto asincrono di Windows Runtime.  
  
### <a name="return-value"></a>Valore restituito  
 Un costrutto asincrono rappresentato da IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^, o IAsyncOperationWithProgress\<TResult, TProgress > ^. L'interfaccia restituita dipende dalla firma dell'espressione lambda passata nella funzione.  
  
### <a name="remarks"></a>Note  
 Il tipo restituito dell'espressione lambda determina se il costrutto è un'azione o un'operazione.  
  
 Le espressioni lambda tramite cui viene restituito void comportano la creazione di azioni. Le espressioni lambda tramite cui viene restituito un risultato di tipo `TResult` comportano la creazione di operazioni TResult.  
  
 L'espressione lambda può inoltre restituire `task<TResult>` che incapsula il lavoro asincrono o è la continuazione di una catena di attività che rappresentano il lavoro asincrono. In questo caso, la stessa espressione lambda viene eseguita inline, poiché le attività sono quelle che vengono eseguite in modo asincrono e viene rimosso il wrapping del tipo restituito dell'espressione lambda per generare il costrutto asincrono restituito da `create_async`. Ciò implica che un'espressione lambda che restituisce un'attività\<void > causerà la creazione di azioni e un'espressione lambda che restituisce un'attività\<TResult > causerà la creazione di operazioni TResult.  
  
 L'espressione lambda può accettare zero, uno o due argomenti. Gli argomenti validi sono `progress_reporter<TProgress>` e `cancellation_token`, in questo ordine se vengono usati entrambi. Un'espressione lambda senza argomenti determina la creazione di un costrutto asincrono senza la funzionalità per la segnalazione dello stato di avanzamento. Un'espressione lambda che accetta un progress_reporter\<TProgress > causerà `create_async` per restituire un costrutto asincrono che segnala lo stato di tipo TProgress ogni volta che il `report` metodo dell'oggetto progress_reporter. Un'espressione lambda che accetta un cancellation_token può usare tale token per verificare l'annullamento oppure passarlo alle attività create in modo che l'annullamento del costrutto asincrono provochi l'annullamento di tali attività.  
  
 Se il corpo dell'oggetto lambda o funzione restituisce un risultato (e non task\<TResult >), l'espressione lambda verrà eseguita in modo asincrono all'interno del processo agente di trasferimento messaggi nel contesto di un'attività, il Runtime crea in modo implicito per esso. Il metodo `IAsyncInfo::Cancel` determina l'annullamento dell'attività implicita.  
  
 Se tramite il corpo di lambda viene restituita un'attività, lambda viene eseguito inline e, dichiarando che nel lambda viene accettato un argomento di tipo `cancellation_token`, è possibile attivare l'annullamento delle attività create all'interno di lambda passando il token quando vengono create. È inoltre possibile usare il metodo `register_callback` sul token per fare in modo che il runtime richiami un callback quando si chiama `IAsyncInfo::Cancel` sull'operazione async o sull'azione prodotta.  
  
 Questa funzione è disponibile solo per le applicazioni Windows Store.  
  
##  <a name="createresourcemanager"></a>CreateResourceManager  
 Restituisce un'interfaccia che rappresenta l'istanza singleton di Gestione risorse del runtime di concorrenza. Gestione risorse è responsabile dell'assegnazione di risorse a utilità di pianificazione che vogliono cooperare tra loro.  
  
```
IResourceManager* __cdecl CreateResourceManager();
```  
  
### <a name="return-value"></a>Valore restituito  
 Interfaccia di `IResourceManager`.  
  
### <a name="remarks"></a>Note  
 Più chiamate successive a questo metodo restituirà la stessa istanza di gestione risorse. Ogni chiamata al metodo incrementa un riferimento contare su Gestione risorse e deve essere associata a una chiamata al [IResourceManager:: Release](http://msdn.microsoft.com/en-us/5d1356ec-fbd3-4284-a361-1e9e20bbb522) metodo quando l'utilità di pianificazione viene eseguita la comunicazione con il gestore delle risorse.  
  
 [unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal Runtime di concorrenza.  
  
##  <a name="create_task"></a>create_task  
 Crea una libreria PPL [attività](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f) oggetto. `create_task` può essere usato ovunque si sarebbe usato un costruttore di attività. Viene fornito principalmente per comodità, in quanto consente l'uso della parola chiave `auto` durante la creazione delle attività.  
  
```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Tipo del parametro dal quale deve essere costruita l'attività.  
  
 `_ReturnType`  
 `_Param`  
 Parametro dal quale deve essere costruita l'attività. Potrebbe trattarsi di un oggetto lambda o funzione, un `task_completion_event` oggetto, un altro `task` oggetto o un'interfaccia Windows::Foundation::IAsyncInfo se si utilizzano attività nell'applicazione Windows Store.  
  
 `_TaskOptions`  
 `_Task`  
  
### <a name="return-value"></a>Valore restituito  
 Una nuova attività di tipo `T`, che è derivato da `_Param`.  
  
### <a name="remarks"></a>Note  
 Il primo overload si comporta come un costruttore di attività che accetta un singolo parametro.  
  
 Il secondo overload associa il token di annullamento fornito con l'attività appena creata. Se si utilizza questo overload non è consentito passare in un altro `task` oggetto come primo parametro.  
  
 Il tipo dell'attività restituita viene dedotto dal primo parametro alla funzione. Se `_Param` è un `task_completion_event<T>`, `task<T>`, o un functor che restituisce dei tipi `T` o `task<T>`, il tipo di attività creata è `task<T>`.  
  
 In un'applicazione Windows Store, se `_Param` è di tipo Windows::Foundation::IAsyncOperation\<T > ^ o Windows::Foundation::IAsyncOperationWithProgress\<T, P > ^, o functor che restituisce uno di questi tipi, l'attività creata sarà di tipo `task<T>`. Se `_Param` è di tipo Windows::Foundation::IAsyncAction ^ o Windows::Foundation::IAsyncActionWithProgress\<P > ^, o functor che restituisce uno di questi tipi, l'attività creata verrà dispone del tipo `task<void>`.  
  
##  <a name="disabletracing"></a>DisableTracing  
 Disabilita la tracciatura nel runtime di concorrenza. Questa funzione è deprecata poiché la traccia ETW non viene registrata per impostazione predefinita.  
  
```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```  
  
### <a name="return-value"></a>Valore restituito  
 Se la traccia è stata correttamente disattivata, `S_OK` viene restituito. Se la traccia non è stata iniziata in precedenza, viene restituito `E_NOT_STARTED`.  
  
##  <a name="enabletracing"></a>EnableTracing  
 Abilita la tracciatura nel runtime di concorrenza. Questa funzione è deprecata poiché la traccia ETW è ora attivata per impostazione predefinita.  
  
```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```  
  
### <a name="return-value"></a>Valore restituito  
 Se la traccia è stata avviata correttamente, `S_OK` restituito; in caso contrario, `E_NOT_STARTED` viene restituito.  
  
##  <a name="free"></a>Gratuito  
 Rilascia un blocco di memoria precedentemente allocato dal metodo `Alloc` al suballocatore di cache del runtime di concorrenza.  
  
```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```  
  
### <a name="parameters"></a>Parametri  
 `_PAllocation`  
 Puntatore alla memoria precedentemente allocato dal `Alloc` metodo che deve essere liberata. Se il parametro `_PAllocation` è impostata sul valore `NULL`, questo metodo ignorarlo e restituirà immediatamente.  
  
### <a name="remarks"></a>Note  
 Per ulteriori informazioni su quali scenari dell'applicazione possono trarre vantaggio dal suballocatore di cache, vedere [utilità di pianificazione](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="get_ambient_scheduler"></a>get_ambient_scheduler  
  
```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="getexecutioncontextid"></a>GetExecutionContextId  
 Restituisce un identificatore univoco che può essere assegnato a un contesto di esecuzione che implementa l'interfaccia `IExecutionContext`.  
  
```
unsigned int __cdecl GetExecutionContextId();
```  
  
### <a name="return-value"></a>Valore restituito  
 Identificatore univoco per un contesto di esecuzione.  
  
### <a name="remarks"></a>Note  
 Utilizzare questo metodo per ottenere un identificatore per il contesto di esecuzione prima di passare un' `IExecutionContext` interfaccia come parametro a uno dei metodi forniti da Gestione risorse.  
  
##  <a name="getosversion"></a>GetOSVersion  
 Restituisce la versione del sistema operativo.  
  
```
IResourceManager::OSVersion __cdecl GetOSVersion();
```  
  
### <a name="return-value"></a>Valore restituito  
 Valore enumerato che rappresenta il sistema operativo.  
  
### <a name="remarks"></a>Note  
 [unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal Runtime di concorrenza.  
  
##  <a name="getprocessorcount"></a>GetProcessorCount  
 Restituisce il numero dei thread hardware sul sistema sottostante.  
  
```
unsigned int __cdecl GetProcessorCount();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di thread di hardware.  
  
### <a name="remarks"></a>Note  
 [unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal Runtime di concorrenza.  
  
##  <a name="getprocessornodecount"></a>GetProcessorNodeCount  
 Restituisce il numero di nodi NUMA o pacchetti del processore sul sistema sottostante.  
  
```
unsigned int __cdecl GetProcessorNodeCount();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di nodi NUMA o pacchetti del processore.  
  
### <a name="remarks"></a>Note  
 Se il sistema contiene più nodi NUMA dei pacchetti del processore, viene restituito il numero di nodi NUMA, in caso contrario, viene restituito il numero di pacchetti del processore.  
  
 [unsupported_os](unsupported-os-class.md) viene generata se il sistema operativo non è supportato dal Runtime di concorrenza.  
  
##  <a name="getschedulerid"></a>GetSchedulerId  
 Restituisce un identificatore univoco che può essere assegnato a un'utilità di pianificazione che implementa l'interfaccia `IScheduler`.  
  
```
unsigned int __cdecl GetSchedulerId();
```  
  
### <a name="return-value"></a>Valore restituito  
 Identificatore univoco per un'utilità di pianificazione.  
  
### <a name="remarks"></a>Note  
 Utilizzare questo metodo per ottenere un identificatore per l'utilità di pianificazione prima di passare un' `IScheduler` interfaccia come parametro a uno dei metodi forniti da Gestione risorse.  
  
##  <a name="internal_assign_iterators"></a>internal_assign_iterators  
  
```
template<typename T, class _Ax>
template<class _I> 
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```   
  
### <a name="parameters"></a>Parametri  
 `T`  
 `_Ax`  
 `_I`  
 `first`  
 `last`  
  
##  <a name="interruption_point"></a>interruption_point  
 Crea un punto di interruzione per l'annullamento. Se un annullamento è in corso nel contesto in cui questa funzione viene chiamata, questa genererà un'eccezione interna che interrompe l'esecuzione del lavoro parallelo in esecuzione. Se l'annullamento non è in corso, la funzione non esegue alcuna operazione.  
  
```
inline void interruption_point();
```  
  
### <a name="remarks"></a>Note  
 Non è consigliabile rilevare l'eccezione di annullamento interna generata dalla funzione `interruption_point()`. L'eccezione viene rilevata e gestita dal runtime, pertanto se viene rilevata potrebbe comportare un'esecuzione anomala del programma.  
  
##  <a name="is_current_task_group_canceling"></a>is_current_task_group_canceling  
 Restituisce un'informazione che indica se il gruppo di attività attualmente in esecuzione inline sul contesto corrente si trova nel mezzo di un annullamento attivo (o lo sarà a breve). Si noti che se non è presente alcun gruppo di attività in esecuzione inline sul contesto corrente, sarà restituito `false`.  
  
```
bool __cdecl is_current_task_group_canceling();
```  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il gruppo di attività attualmente in esecuzione viene annullato, `false` in caso contrario.  
  
### <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere [annullamento](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="make_choice"></a>make_choice  
 Costruisce un blocco della messaggistica `choice` da un oggetto `Scheduler` o `ScheduleGroup` facoltativo e due o più origini di input.  
  
```
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
 `T1`  
 Tipo di blocco del messaggio della prima origine.  
  
 `T2`  
 Tipo di blocco del messaggio la seconda origine.  
  
 `_PScheduler`  
 Oggetto `Scheduler` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `choice` .  
  
 `_Item1`  
 La prima origine.  
  
 `_Item2`  
 La seconda origine.  
  
 `_Items`  
 Origini supplementari.  
  
 `_PScheduleGroup`  
 Oggetto `ScheduleGroup` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `choice` . L'oggetto `Scheduler` usato è previsto dal gruppo di pianificazione.  
  
### <a name="return-value"></a>Valore restituito  
 Blocco di messaggi `choice` con due o più origini di input.  
  
##  <a name="make_greedy_join"></a>make_greedy_join  
 Costruisce un blocco della messaggistica `greedy multitype_join` da un oggetto `Scheduler` o `ScheduleGroup` facoltativo e due o più origini di input.  
  
```
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
 `T1`  
 Tipo di blocco del messaggio della prima origine.  
  
 `T2`  
 Tipo di blocco del messaggio la seconda origine.  
  
 `_PScheduler`  
 Oggetto `Scheduler` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` .  
  
 `_Item1`  
 La prima origine.  
  
 `_Item2`  
 La seconda origine.  
  
 `_Items`  
 Origini supplementari.  
  
 `_PScheduleGroup`  
 Oggetto `ScheduleGroup` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` . L'oggetto `Scheduler` usato è previsto dal gruppo di pianificazione.  
  
### <a name="return-value"></a>Valore restituito  
 Blocco di messaggi `greedy multitype_join` con due o più origini di input.  
  
##  <a name="make_join"></a>make_join  
 Costruisce un blocco della messaggistica `non_greedy multitype_join` da un oggetto `Scheduler` o `ScheduleGroup` facoltativo e due o più origini di input.  
  
```
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
 `T1`  
 Tipo di blocco del messaggio della prima origine.  
  
 `T2`  
 Tipo di blocco del messaggio la seconda origine.  
  
 `_PScheduler`  
 Oggetto `Scheduler` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` .  
  
 `_Item1`  
 La prima origine.  
  
 `_Item2`  
 La seconda origine.  
  
 `_Items`  
 Origini supplementari.  
  
 `_PScheduleGroup`  
 Oggetto `ScheduleGroup` all'interno del quale è pianificata l'attività di propagazione per il blocco della messaggistica `multitype_join` . L'oggetto `Scheduler` usato è previsto dal gruppo di pianificazione.  
  
### <a name="return-value"></a>Valore restituito  
 Blocco di messaggi `non_greedy multitype_join` con due o più origini di input.  
  
##  <a name="make_task"></a>make_task  
 Un metodo factory per la creazione di un oggetto `task_handle`.  
  
```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametri  
 `_Function`  
 Il tipo dell'oggetto funzione che sarà richiamato per eseguire il lavoro rappresentato dal `task_handle` oggetto.  
  
 `_Func`  
 La funzione che sarà richiamata per eseguire il lavoro rappresentato di `task_handle` oggetto. Può trattarsi di un funtore lambda, un puntatore a una funzione o un qualsiasi oggetto che supporta una versione dell'operatore di chiamata di funzione con la firma `void operator()()`.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto `task_handle`.  
  
### <a name="remarks"></a>Note  
 Questa funzione è utile quando è necessario creare un `task_handle` dell'oggetto con un'espressione lambda, perché consente di creare l'oggetto senza sapere il vero tipo del funtore lambda.  
  
##  <a name="parallel_buffered_sort"></a>parallel_buffered_sort  
 Dispone gli elementi in un intervallo specificato in un ordine non decrescente, o secondo un criterio di ordinamento specificato da un predicato binario, in parallelo. Questa funzione è semanticamente simile a `std::sort` in quanto si tratta di un ordinamento basato sul confronto, instabile, sul posto, ma richiede uno spazio aggiuntivo pari `O(n)` e l'inizializzazione predefinita per gli elementi in fase di ordinamento.  
  
```
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
 `_Random_iterator`  
 Tipo dell'iteratore dell'intervallo di input.  
  
 `_Allocator`  
 Il tipo di allocatore di memoria compatibile della libreria Standard C++.  
  
 `_Function`  
 Il tipo di confronto binario.  
  
 `_Begin`  
 Iteratore ad accesso casuale che punta alla posizione del primo elemento nell'intervallo da ordinare.  
  
 `_End`  
 Iteratore ad accesso casuale che punta alla prima posizione oltre l'elemento finale nell'intervallo da ordinare.  
  
 `_Alloc`  
 Un'istanza di un allocatore di memoria compatibile della libreria Standard C++.  
  
 `_Func`  
 Oggetto funzione predicato definito dall'utente tramite cui vengono definiti i criteri di confronto che devono essere soddisfatti dagli elementi successivi nell'ordinamento. Un predicato binario accetta due argomenti e viene restituito `true` se la condizione è soddisfatta e `false` se non lo è. Tramite questa funzione di confronto deve essere imposto un ordinamento di tipo "strict weak" alle coppie di elementi della sequenza.  
  
 `_Chunk_size`  
 Dimensione minima di un blocco che verrà suddiviso in due per l'esecuzione parallela.  
  
### <a name="remarks"></a>Note  
 Tutti gli overload richiedono `n * sizeof(T)` ulteriore spazio, in cui `n` è il numero di elementi da ordinare e `T` è il tipo di elemento. Nella maggior parte dei casi parallel_buffered_sort mostrerà un miglioramento delle prestazioni su [parallel_sort](concurrency-namespace-functions.md), ed è consigliabile utilizzarlo su parallel_sort se si dispone di memoria disponibile.  
  
 Se non si fornisce un confronto binario `std::less` viene utilizzato come impostazione predefinita, che richiede il tipo di elemento fornire l'operatore `operator<()`.  
  
 Se non si specifica un tipo di allocatore o un'istanza, l'allocatore di memoria della libreria Standard C++ `std::allocator<T>` viene utilizzato per allocare il buffer.  
  
 Tramite l'algoritmo l'intervallo di input viene diviso in due blocchi e successivamente ogni blocco viene diviso in due blocchi secondari per l'esecuzione in parallelo. L'argomento facoltativo `_Chunk_size` può essere utilizzato per indicare all'algoritmo che i blocchi di dimensione < `_Chunk_size` devono essere gestiti in serie.  
  
##  <a name="parallel_for"></a>parallel_for  
 `parallel_for` viene iterato su un intervallo di indici ed esegue una funzione fornita dall'utente a ogni iterazione, in parallelo.  
  
```
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
 `_Index_type`  
 Il tipo di indice utilizzato per l'iterazione.  
  
 `_Function`  
 Il tipo della funzione che verrà eseguito a ogni iterazione.  
  
 `_Partitioner`  
 Il tipo di partitioner che viene utilizzato per dividere l'intervallo specificato.  
  
 `first`  
 Il primo indice da includere nell'iterazione.  
  
 `last`  
 L'indice uno dopo l'ultimo indice da includere nell'iterazione.  
  
 `_Step`  
 Valore per il quale è possibile eseguire durante l'iterazione da `first` a `last`. Il passaggio deve essere positivo. [invalid_argument](../../../standard-library/invalid-argument-class.md) viene generata se il passaggio è minore di 1.  
  
 `_Func`  
 La funzione venga eseguita a ogni iterazione. Potrebbe essere un'espressione lambda, un puntatore a funzione, o qualsiasi altro oggetto che supporta una versione dell'operatore di chiamata di funzione con la firma `void operator()(``_Index_type``)`.  
  
 `_Part`  
 Riferimento all'oggetto partitioner. L'argomento può essere uno dei `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` o [affinity_partitioner](affinity-partitioner-class.md) `&` se un [affinity_partitioner](affinity-partitioner-class.md) oggetto viene utilizzato, il riferimento deve essere un riferimento di valore l-value non const, in modo che l'algoritmo di archiviare lo stato per riutilizzare nei cicli futuri.  
  
### <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere [algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_for_each"></a>parallel_for_each  
 `parallel_for_each` applica una funzione specificata a ogni elemento all'interno di un intervallo, in parallelo. È semanticamente equivalente alla funzione `for_each` nello spazio dei nomi `std`, fatta eccezione per l'iterazione sugli elementi, che viene eseguita in parallelo, e per l'ordine di iterazione, che non è specificato. L'argomento `_Func` deve supportare un operatore di chiamata della funzione del form `operator()(T)` laddove il parametro `T` è il tipo di elemento del contenitore su cui viene eseguita l'iterazione.  
  
```
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
 `_Iterator`  
 Il tipo di iteratore utilizzato per scorrere il contenitore.  
  
 `_Function`  
 Il tipo della funzione che verrà applicato a ogni elemento all'interno dell'intervallo.  
  
 `_Partitioner`  
 `first`  
 Un iteratore che punta alla posizione del primo elemento da includere in iterazione parallela.  
  
 `last`  
 Un iteratore che punta alla posizione immediatamente successiva all'ultimo elemento da includere in iterazione parallela.  
  
 `_Func`  
 Un oggetto funzione definita dall'utente che viene applicato a ogni elemento nell'intervallo.  
  
 `_Part`  
 Riferimento all'oggetto partitioner. L'argomento può essere uno dei `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` o [affinity_partitioner](affinity-partitioner-class.md) `&` se un [affinity_partitioner](affinity-partitioner-class.md) oggetto viene utilizzato, il riferimento deve essere un riferimento di valore l-value non const, in modo che l'algoritmo di archiviare lo stato per riutilizzare nei cicli futuri.  
  
### <a name="remarks"></a>Note  
 [auto_partitioner](auto-partitioner-class.md) verrà utilizzato per l'overload senza un partitioner esplicito.  
  
 Per gli iteratori che non supportano casuale, solo accesso [auto_partitioner](auto-partitioner-class.md) è supportato.  
  
 Per ulteriori informazioni, vedere [algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_invoke"></a>Parallel. Invoke  
 Esegue gli oggetti funzione forniti come parametri in parallelo e blocca fino al termine dell'esecuzione. Ogni oggetto funzione potrebbe essere un'espressione lambda, un puntatore a funzione o qualsiasi oggetto che supporta l'operatore della chiamata di funzione con la firma `void operator()()`.  
  
```
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
 `_Function1`  
 Il tipo del primo oggetto funzione da eseguire in parallelo.  
  
 `_Function2`  
 Il tipo del secondo oggetto funzione da eseguire in parallelo.  
  
 `_Function3`  
 Il tipo del terzo oggetto funzione da eseguire in parallelo.  
  
 `_Function4`  
 Il tipo del quarto oggetto funzione da eseguire in parallelo.  
  
 `_Function5`  
 Il tipo del quinto oggetto funzione da eseguire in parallelo.  
  
 `_Function6`  
 Il tipo del sesto oggetto funzione da eseguire in parallelo.  
  
 `_Function7`  
 Il tipo del settimo oggetto funzione da eseguire in parallelo.  
  
 `_Function8`  
 Il tipo dell'ottavo oggetto funzione da eseguire in parallelo.  
  
 `_Function9`  
 Il tipo del nono oggetto funzione da eseguire in parallelo.  
  
 `_Function10`  
 Il tipo del decimo oggetto funzione da eseguire in parallelo.  
  
 `_Func1`  
 Primo oggetto funzione da eseguire in parallelo.  
  
 `_Func2`  
 Secondo oggetto funzione da eseguire in parallelo.  
  
 `_Func3`  
 Terzo oggetto funzione da eseguire in parallelo.  
  
 `_Func4`  
 Quarto oggetto funzione da eseguire in parallelo.  
  
 `_Func5`  
 Il quinto oggetto funzione da eseguire in parallelo.  
  
 `_Func6`  
 Il sesto oggetto funzione da eseguire in parallelo.  
  
 `_Func7`  
 Il settimo oggetto funzione da eseguire in parallelo.  
  
 `_Func8`  
 L'ottavo oggetto funzione da eseguire in parallelo.  
  
 `_Func9`  
 Il nono oggetto funzione da eseguire in parallelo.  
  
 `_Func10`  
 Decimo oggetto funzione da eseguire in parallelo.  
  
### <a name="remarks"></a>Note  
 Si noti che uno o più degli oggetti funzione forniti come parametri possono essere eseguiti inline nel contesto di chiamata.  
  
 Se uno o più degli oggetti funzione passati come parametri a questa funzione genera un'eccezione, il runtime un'eccezione di questo tipo di scelta e propagherà dalla chiamata a `parallel_invoke`.  
  
 Per ulteriori informazioni, vedere [algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_radixsort"></a>parallel_radixsort  
 Dispone gli elementi in un intervallo specificato in un ordine non decrescente usando l'algoritmo Radix Sort. Si tratta di una funzione stabile di ordinamento che richiede una funzione di proiezione affinché che consente agli elementi del progetto di essere ordinati nelle chiavi di tipo intero senza segno. L'inizializzazione predefinita è necessaria per gli elementi da ordinare.  
  
```
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
 `_Random_iterator`  
 Tipo dell'iteratore dell'intervallo di input.  
  
 `_Allocator`  
 Il tipo di allocatore di memoria compatibile della libreria Standard C++.  
  
 `_Function`  
 Il tipo della funzione di proiezione.  
  
 `_Begin`  
 Iteratore ad accesso casuale che punta alla posizione del primo elemento nell'intervallo da ordinare.  
  
 `_End`  
 Iteratore ad accesso casuale che punta alla prima posizione oltre l'elemento finale nell'intervallo da ordinare.  
  
 `_Alloc`  
 Un'istanza di un allocatore di memoria compatibile della libreria Standard C++.  
  
 `_Proj_func`  
 Un oggetto funzione di proiezione definito dall'utente che converte un elemento in un valore integrale.  
  
 `_Chunk_size`  
 Dimensione minima di un blocco che verrà suddiviso in due per l'esecuzione parallela.  
  
### <a name="remarks"></a>Note  
 Tutti gli overload richiedono `n * sizeof(T)` ulteriore spazio, in cui `n` è il numero di elementi da ordinare e `T` è il tipo di elemento. Un funtore proiezione unario con la firma `I _Proj_func(T)` è necessaria per restituire una chiave quando viene specificato un elemento, in cui `T` è il tipo di elemento e `I` è un tipo simile a valore integer senza segno.  
  
 Se non si specifica una funzione di proiezione, una funzione di proiezione predefinita che restituisce semplicemente l'elemento viene utilizzata per i tipi integrali. La funzione di compilazione non verrà completata se l'elemento non è un tipo integrale in assenza di una funzione di proiezione.  
  
 Se non si specifica un tipo di allocatore o un'istanza, l'allocatore di memoria della libreria Standard C++ `std::allocator<T>` viene utilizzato per allocare il buffer.  
  
 Tramite l'algoritmo l'intervallo di input viene diviso in due blocchi e successivamente ogni blocco viene diviso in due blocchi secondari per l'esecuzione in parallelo. L'argomento facoltativo `_Chunk_size` può essere utilizzato per indicare all'algoritmo che i blocchi di dimensione < `_Chunk_size` devono essere gestiti in serie.  
  
##  <a name="parallel_reduce"></a>parallel_reduce  
 Calcola la somma di tutti gli elementi in un intervallo specificato elaborando le somme parziali successive, o calcola il risultato dei risultati parziali successivi ottenuti analogamente tramite l'uso di un'operazione binaria specificata diversa da quella di somma, in parallelo. `parallel_reduce` è semanticamente simile a `std::accumulate`, con la differenza che richiede all'operazione binaria di essere associativa e richiede un valore di identità anziché un valore iniziale.  
  
```
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
 `_Forward_iterator`  
 Tipo dell'iteratore dell'intervallo di input.  
  
 `_Sym_reduce_fun`  
 Il tipo della funzione di riduzione simmetrica. Deve trattarsi di un tipo di funzione con firma `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, dove _Reduce_type è lo stesso tipo di identità e il tipo di risultato della riduzione. Per il terzo overload deve essere coerenza con il tipo di output di `_Range_reduce_fun`.  
  
 `_Reduce_type`  
 Tipo che consenta di ridurre l'input, che può essere diverso dal tipo di elemento di input. Il valore restituito e il valore di identità verranno dispone di questo tipo.  
  
 `_Range_reduce_fun`  
 Il tipo della funzione di riduzione intervallo. Deve trattarsi di un tipo di funzione con firma `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type è lo stesso tipo di identità e il tipo di risultato della riduzione.  
  
 `_Begin`  
 Un iteratore di input punta al primo elemento nell'intervallo da ridurre.  
  
 `_End`  
 Un iteratore di input che punta all'elemento che è una posizione successiva all'ultimo elemento nell'intervallo da ridotto.  
  
 `_Identity`  
 Il valore identity `_Identity` è dello stesso tipo del tipo di risultato della riduzione e anche il `value_type` dell'iteratore per il primo e il secondo overload. Per il terzo overload, il valore di identità devono avere lo stesso tipo del tipo di risultato della riduzione, ma possono essere diverso dal `value_type` dell'iteratore. Deve avere un valore appropriato in modo che l'operatore di riduzione intervallo `_Range_fun`, quando applicato a un intervallo di un singolo elemento di tipo `value_type` e il valore di identità, si comporta come un cast di tipo del valore di tipo `value_type` per il tipo di identità.  
  
 `_Sym_fun`  
 La funzione simmetrica che verrà utilizzata il secondo della riduzione. Per ulteriori informazioni, consultare la sezione Osservazioni.  
  
 `_Range_fun`  
 La funzione che verrà utilizzata nella prima fase della riduzione. Per ulteriori informazioni, consultare la sezione Osservazioni.  
  
### <a name="return-value"></a>Valore restituito  
 Il risultato della riduzione.  
  
### <a name="remarks"></a>Note  
 Per eseguire una riduzione parallela, la funzione divide l'intervallo in blocchi in base al numero di thread di lavoro disponibili per l'utilità di pianificazione sottostante. La riduzione avviene in due fasi, la prima fase esegue una riduzione all'interno di ogni blocco e la seconda fase esegue una riduzione tra i risultati parziali da ogni blocco.  
  
 Il primo overload richiede che l'iteratore `value_type`, `T`, essere uguale a come il tipo di valore di identità, nonché il tipo di risultato di riduzione. Il tipo di elemento T deve fornire l'operatore `T T::operator + (T)` per ridurre gli elementi in ogni blocco. Nella seconda fase viene utilizzato l'operatore stesso.  
  
 Il secondo overload richiede inoltre che l'iteratore `value_type` corrispondere esattamente il tipo di valore di identità, nonché il tipo di risultato di riduzione. L'operatore binario fornito `_Sym_fun` viene utilizzato in entrambe le fasi di riduzione, con il valore di identità come il valore iniziale per la prima fase.  
  
 Per il terzo overload, il tipo di valore di identità deve essere lo stesso come il tipo di risultato di riduzione, ma l'iteratore `value_type` potrebbe essere diverso da entrambi. La funzione di riduzione intervallo `_Range_fun` viene utilizzato nella prima fase con il valore di identità come il valore iniziale e la funzione binario `_Sym_reduce_fun` viene applicata per sub risultati nella seconda fase.  
  
##  <a name="parallel_sort"></a>parallel_sort  
 Dispone gli elementi in un intervallo specificato in un ordine non decrescente, o secondo un criterio di ordinamento specificato da un predicato binario, in parallelo. Questa funzione è semanticamente simile a `std::sort` in quanto si tratta di un ordinamento basato sul confronto, instabile, sul posto.  
  
```
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
 `_Random_iterator`  
 Tipo dell'iteratore dell'intervallo di input.  
  
 `_Function`  
 Tipo del funtore di confronto binario.  
  
 `_Begin`  
 Iteratore ad accesso casuale che punta alla posizione del primo elemento nell'intervallo da ordinare.  
  
 `_End`  
 Iteratore ad accesso casuale che punta alla prima posizione oltre l'elemento finale nell'intervallo da ordinare.  
  
 `_Func`  
 Oggetto funzione predicato definito dall'utente tramite cui vengono definiti i criteri di confronto che devono essere soddisfatti dagli elementi successivi nell'ordinamento. Un predicato binario accetta due argomenti e viene restituito `true` se la condizione è soddisfatta e `false` se non lo è. Tramite questa funzione di confronto deve essere imposto un ordinamento di tipo "strict weak" alle coppie di elementi della sequenza.  
  
 `_Chunk_size`  
 Dimensione minima di un blocco che verrà suddiviso in due per l'esecuzione parallela.  
  
### <a name="remarks"></a>Note  
 Nel primo overload viene utilizzato il confronto binario `std::less`.  
  
 Nel secondo overload viene utilizzato il confronto binario fornito in cui deve essere presente la firma `bool _Func(T, T)` dove `T` è il tipo degli elementi dell'intervallo di input.  
  
 Tramite l'algoritmo l'intervallo di input viene diviso in due blocchi e successivamente ogni blocco viene diviso in due blocchi secondari per l'esecuzione in parallelo. L'argomento facoltativo `_Chunk_size` può essere utilizzato per indicare all'algoritmo che i blocchi di dimensione < `_Chunk_size` devono essere gestiti in serie.  
  
##  <a name="parallel_transform"></a>parallel_transform  
 Applica un oggetto funzione specificato ad ogni elemento di un intervallo di origine o a una coppia di elementi di due intervalli di origine e copia i valori restituiti dell'oggetto funzione in un intervallo di destinazione, in parallelo. Questa funzione è semanticamente equivalente a `std::transform`.  
  
```
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
 `_Input_iterator1`  
 Tipo del primo iteratore o di quello solo di input.  
  
 `_Output_iterator`  
 Il tipo di iteratore di output.  
  
 `_Unary_operator`  
 Tipo del funtore unario che deve essere eseguito in ogni elemento nell'intervallo di input.  
  
 `_Input_iterator2`  
 Tipo del secondo iteratore di input.  
  
 `_Binary_operator`  
 Tipo del funtore binario eseguito a livello pairwise negli elementi di due intervalli di origine.  
  
 `_Partitioner`  
 `first1`  
 Iteratore di input che punta alla posizione del primo elemento nel primo intervallo o in quello solo origine da utilizzare.  
  
 `last1`  
 Iteratore di input che punta alla prima posizione dopo l'elemento finale nel primo intervallo o in quello solo di origine da utilizzare.  
  
 `_Result`  
 Iteratore di output che punta alla posizione del primo elemento nell'intervallo di destinazione.  
  
 `_Unary_op`  
 Oggetto funzione unario definito dall'utente che viene applicato a ogni elemento nell'intervallo di origine.  
  
 `_Part`  
 Riferimento all'oggetto partitioner. L'argomento può essere uno dei `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` o [affinity_partitioner](affinity-partitioner-class.md) `&` se un [affinity_partitioner](affinity-partitioner-class.md) oggetto viene utilizzato, il riferimento deve essere un riferimento di valore l-value non const, in modo che l'algoritmo di archiviare lo stato per riutilizzare nei cicli futuri.  
  
 `first2`  
 Iteratore di input che punta alla posizione del primo elemento nel secondo intervallo di origine da utilizzare.  
  
 `_Binary_op`  
 Oggetto funzione binario definito dall'utente applicato a livello pairwise, in ordine progressivo, ai due intervalli di origine.  
  
### <a name="return-value"></a>Valore restituito  
 Iteratore di output che punta alla prima posizione dopo l'elemento finale nell'intervallo di destinazione in cui vengono ricevuti gli elementi di output trasformati dall'oggetto funzione.  
  
### <a name="remarks"></a>Note  
 [auto_partitioner](auto-partitioner-class.md) verrà utilizzato per gli overload senza un argomento partitioner esplicito.  
  
 Per gli iteratori che non supportano casuale, solo accesso [auto_partitioner](auto-partitioner-class.md) è supportato.  
  
 Tramite gli overload che accettano l'argomento `_Unary_op` l'intervallo di input viene trasformato in quello di output applicando il funtore unario a ogni elemento nell'intervallo di input. `_Unary_op` deve supportare l'operatore di chiamata di funzione con la firma `operator()(T)` dove `T` è il tipo di valore dell'intervallo che viene scorso.  
  
 Tramite gli overload che accettano l'argomento `_Binary_op` i due intervalli di input vengono trasformati nell'intervallo di output applicando il funtore binario a un elemento del primo intervallo di input e a un elemento dal secondo. `_Binary_op` deve supportare l'operatore di chiamata di funzione con la firma `operator()(T, U)` dove `T` e `U` sono i tipi di valori dei due iteratori di input.  
  
 Per ulteriori informazioni, vedere [algoritmi paralleli](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="receive"></a>ricezione  
 Un'implementazione di ricezione generale, che consente a un contesto di attendere i dati esattamente da un'origine e di filtrare i valori accettati.  
  
```
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
 `T`  
 Il tipo di payload.  
  
 `_Src`  
 Un puntatore o un riferimento all'origine da cui sono previsti dati.  
  
 `_Timeout`  
 Il tempo massimo per il quale il metodo necessario per i dati, in millisecondi.  
  
 `_Filter_proc`  
 Una funzione di filtro che determina se i messaggi devono essere accettati.  
  
### <a name="return-value"></a>Valore restituito  
 Un valore dall'origine, il tipo di payload.  
  
### <a name="remarks"></a>Note  
 Se il parametro `_Timeout` ha un valore diverso dalla costante `COOPERATIVE_TIMEOUT_INFINITE`, l'eccezione [operation_timed_out](operation-timed-out-class.md) viene generata se la quantità specificata di tempo scade prima che venga ricevuto un messaggio. Se si desidera un timeout di lunghezza zero, è necessario utilizzare il [try_receive](concurrency-namespace-functions.md) funzione, anziché chiamare il metodo `receive` con un timeout di `0` (zero), perché è più efficiente e non genera eccezioni sui timeout.  
  
 Per ulteriori informazioni, vedere [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="run_with_cancellation_token"></a>run_with_cancellation_token  
 Esegue un oggetto funzione immediatamente e in modo sincrono nel contesto di uno specifico token di annullamento.  
  
```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```  
  
### <a name="parameters"></a>Parametri  
 `_Function`  
 Tipo dell'oggetto funzione che sarà richiamato.  
  
 `_Func`  
 Oggetto funzione che verrà eseguito. Questo oggetto deve supportare l'operatore di chiamata di funzione con una firma void(void).  
  
 `_Ct`  
 Token di annullamento tramite cui verrà controllato l'annullamento implicito dell'oggetto funzione. Utilizzare `cancellation_token::none()` se si desidera che la funzione venga eseguita senza alcuna possibilità di annullamento implicito da un gruppo di attività padre che viene annullato.  
  
### <a name="remarks"></a>Note  
 Quando l'oggetto `cancellation_token` viene annullato, verranno attivati tutti i punti di interruzione nell'oggetto funzione. Tramite il token esplicito `_Ct` questo parametro `_Func` verrà isolato dall'annullamento padre se al padre è associato un token diverso o se non ne dispone.  
  
##  <a name="send"></a>Invia  
 Un'operazione di invio sincrona che attende fino a quando la destinazione accetta o rifiuta il messaggio.  
  
```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di payload.  
  
 `_Trg`  
 Un puntatore o un riferimento alla destinazione a cui i dati vengono inviati.  
  
 `_Data`  
 Riferimento ai dati da inviare.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il messaggio è stato accettato, `false` in caso contrario.  
  
### <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="set_ambient_scheduler"></a>set_ambient_scheduler  
  
```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```  
  
### <a name="parameters"></a>Parametri  
 `_Scheduler`  
  
##  <a name="set_task_execution_resources"></a>set_task_execution_resources  
 Limita le risorse di esecuzione usate dai thread di lavoro interni del runtime di concorrenza al set di affinità specificato.  
  
 È valido chiamare questo metodo solo prima della creazione di Gestione risorse o tra due cicli di vita di Gestione risorse. Può essere chiamato più volte a condizione che Gestione risorse non esista al momento della chiamata. Dopo aver impostato un limite di affinità, rimane attiva fino alla successiva chiamata al metodo `set_task_execution_resources`.  
  
 La maschera di affinità fornita non deve essere un sottoinsieme della maschera di affinità del processo. L'affinità del processo verrà aggiornata, se necessario.  
  
```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```  
  
### <a name="parameters"></a>Parametri  
 `_ProcessAffinityMask`  
 Maschera di affinità in base alla quale devono essere limitati i thread di lavoro del runtime di concorrenza. Utilizzare questo metodo in un sistema con più di 64 thread hardware solo se si desidera limitare il runtime di concorrenza a un subset del gruppo di processori correnti. In genere, è necessario utilizzare la versione del metodo che accetta una matrice di affinità di gruppo come parametro, per limitare l'affinità in computer con più di 64 thread hardware.  
  
 `count`  
 Numero di voci `GROUP_AFFINITY` nella matrice specificata dal parametro `_PGroupAffinity`.  
  
 `_PGroupAffinity`  
 Matrice di voci `GROUP_AFFINITY`.  
  
### <a name="remarks"></a>Note  
 Il metodo genererà un [invalid_operation](invalid-operation-class.md) eccezione se è presente al momento viene richiamato un gestore di risorse e un [invalid_argument](../../../standard-library/invalid-argument-class.md) eccezione se l'affinità specificata in un set vuoto di risorse.  
  
 La versione del metodo che accetta una matrice di affinità di gruppo come parametro deve essere utilizzata solo nei sistemi operativi con versione Windows 7 o superiore. In caso contrario, un [invalid_operation](invalid-operation-class.md) viene generata un'eccezione.  
  
 La modifica dell'affinità di processo a livello di codice dopo che questo metodo è stato richiamato comporta la mancata rivalutazione da parte di Gestione Risorse dell'affinità a cui è limitato. Pertanto, tutte le modifiche all'affinità di processo devono essere realizzate prima di chiamare questo metodo.  
  
##  <a name="swap"></a>  swap  
 Scambia gli elementi di due oggetti `concurrent_vector`.  
  
```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati degli elementi archiviati nel vettore simultaneo.  
  
 `_Ax`  
 Il tipo di allocatore dei vettori simultanei.  
  
 `_A`  
 Il vettore simultaneo i cui elementi sono da scambiare con quelli del vettore simultaneo `_B`.  
  
 `_B`  
 Il vettore simultaneo fornisce gli elementi da scambiare o vettore i cui elementi sono da scambiare con quelli del vettore simultaneo `_A`.  
  
### <a name="remarks"></a>Note  
 La funzione di modello è un algoritmo specializzato per la classe contenitore `concurrent_vector` per eseguire la funzione membro `_A`. [concurrent_vector:: swap](concurrent-vector-class.md#swap)( `_B`). Si tratta di istanze di ordinamento parziale dei modelli di funzione da parte del compilatore. Quando le funzioni modello sono sottoposte a overload in modo tale che la corrispondenza del modello con la chiamata di funzione non è univoca, il compilatore seleziona la versione più specializzata della funzione modello. La versione generale della funzione di modello, `template <class T> void swap(T&, T&)`, nell'algoritmo classe funziona tramite assegnazione ed è un'operazione lenta. La versione specializzata presente in ogni contenitore è molto più veloce, dal momento che funziona con la rappresentazione interna della classe contenitore.  
  
 Questo metodo non è indipendente dalla concorrenza. È necessario assicurarsi che nessun altro thread eseguono operazioni su uno dei vettori simultanei quando si chiama questo metodo.  
  
##  <a name="task_from_exception"></a>task_from_exception  
  
```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>Parametri  
 `_TaskType`  
 `_ExType`  
 `_Exception`  
 `_TaskOptions`  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="task_from_result"></a>task_from_result  
  
```
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 `_Param`  
 `_TaskOptions`  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="trace_agents_register_name"></a>Trace_agents_register_name  
 Associa il nome specificato con il blocco di messaggi o l'agente nella traccia ETW.  
  
```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Tipo dell'oggetto. Si tratta in genere di un blocco di messaggi o di un agente.  
  
 `_PObject`  
 Puntatore al blocco di messaggi o all'agente che viene denominato nella traccia.  
  
 `_Name`  
 Nome dell'oggetto fornito.  
  
##  <a name="try_receive"></a>try_receive  
 Un'implementazione di ricezione try generale, che consente a un contesto di cercare i dati esattamente da un'origine e di filtrare i valori accettati. Se i dati non sono pronti, il metodo restituirà false.  
  
``` 
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
 `T`  
 Il tipo di payload  
  
 `_Src`  
 Un puntatore o un riferimento all'origine da cui sono previsti dati.  
  
 `_value`  
 Un riferimento a una posizione in cui verrà inserito il risultato.  
  
 `_Filter_proc`  
 Una funzione di filtro che determina se i messaggi devono essere accettati.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto `bool` valore che indica se è stato inserito in un payload `_value`.  
  
### <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere [Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="wait"></a>attesa  
 Consente di sospendere il contesto corrente per un intervallo di tempo specificato.  
  
```
void __cdecl wait(unsigned int _Milliseconds);
```  
  
### <a name="parameters"></a>Parametri  
 `_Milliseconds`  
 Numero di millisecondi durante i quali il contesto corrente deve essere sospeso. Se il parametro `_Milliseconds` viene impostato sul valore `0`, il contesto corrente deve essere eseguito in altri contesti eseguibili prima di continuare.  
  
### <a name="remarks"></a>Note  
 Se questo metodo viene chiamato in un contesto dell'utilità di pianificazione del Runtime di concorrenza, l'utilità di pianificazione troverà un contesto diverso da eseguire sulla risorsa sottostante. Poiché l'utilità di pianificazione è cooperativa di natura, non è possibile riprendere il contesto subito dopo il numero di millisecondi specificati. Se tramite l'utilità di pianificazione vengono eseguite altre attività che non vengono passate in modo cooperativo all'utilità, il periodo di attesa potrebbe essere indefinito.  
  
##  <a name="when_all"></a>when_all  
 Crea un'attività che verrà completata correttamente quando tutte le attività fornite come argomenti verranno completate.  
  
```
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) -> 
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```   
  
### <a name="parameters"></a>Parametri  
 `_Iterator`  
 Tipo di iteratore di input.  
  
 `_Begin`  
 Posizione del primo elemento nell'intervallo di elementi da combinare nell'attività risultante.  
  
 `_End`  
 Posizione del primo elemento oltre l'intervallo di elementi da combinare nell'attività risultante.  
  
 `_TaskOptions`  
  
### <a name="return-value"></a>Valore restituito  
 Attività che viene completata correttamente quando tutte le attività di input sono state completate. Se le attività di input sono di tipo `T`, l'output di questa funzione sarà `task<std::vector<T>>`. Se le attività di input sono di tipo `void`, anche l'attività di output sarà `task<void>`.  
  
### <a name="remarks"></a>Note  
 `when_all` è una funzione non bloccante che produce `task` come risultato. A differenza di [Task:: Wait](task-class.md#wait), è consigliabile chiamare questa funzione un [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] app nel thread ASTA (Application STA).  
  
 Se una delle attività è stata annullata o genera un'eccezione, l'attività restituita verrà completata in anticipo, nello stato annullato, e l'eccezione, se ne è presente una, verrà generata se si chiama [Task:: Get](task-class.md#get) o `task::wait` sull'attività in questione.  
  
 Per ulteriori informazioni, vedere [parallelismo delle attività](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="when_any"></a>when_any  
 Crea un'attività che verrà completata correttamente quando una qualsiasi delle attività fornite come argomenti verrà completata.  
  
```
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
 `_Iterator`  
 Tipo di iteratore di input.  
  
 `_Begin`  
 Posizione del primo elemento nell'intervallo di elementi da combinare nell'attività risultante.  
  
 `_End`  
 Posizione del primo elemento oltre l'intervallo di elementi da combinare nell'attività risultante.  
  
 `_TaskOptions`  
 `_CancellationToken`  
 Token di annullamento che controlla l'annullamento dell'attività restituita. Se non si fornisce un token di annullamento, l'attività risultante riceverà il token di annullamento dell'attività che ne causa il completamento.  
  
### <a name="return-value"></a>Valore restituito  
 Attività che viene completata correttamente quando una delle attività di input è stata completata. Se le attività di input sono di tipo `T`, l'output di questa funzione sarà un `task<std::pair<T, size_t>>>`, dove il primo elemento della coppia è il risultato dell'attività in corso di completamento e il secondo elemento è l'indice dell'attività completata. Se le attività di input sono di tipo `void` l'output è un `task<size_t>`, dove il risultato è l'indice dell'attività in corso di completamento.  
  
### <a name="remarks"></a>Note  
 `when_any` è una funzione non bloccante che produce `task` come risultato. A differenza di [Task:: Wait](task-class.md#wait), è consigliabile chiamare questa funzione un [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] app nel thread ASTA (Application STA).  
  
 Per ulteriori informazioni, vedere [parallelismo delle attività](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)
