---
title: AsyncBase (classe)
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 0254aa4dc243eeffa43850c437a833a6530c01e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371869"
---
# <a name="asyncbase-class"></a>AsyncBase (classe)

Implementa la macchina a stati asincrona di Windows Runtime.

## <a name="syntax"></a>Sintassi

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parametri

*Completamento TComplete*<br/>
Gestore eventi chiamato al completamento di un'operazione asincrona.

*Tprogress*<br/>
Gestore eventi chiamato quando un'operazione asincrona in esecuzione segnala lo stato corrente dell'operazione.

*Resulttype*<br/>
Uno dei valori di enumerazione [AsyncResultType.](asyncresulttype-enumeration.md) Per impostazione predefinita, `SingleResult`.

## <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

Nome                               | Descrizione
---------------------------------- | -------------------------------------------------
[AsyncBase::AsyncBase](#asyncbase) | Inizializza un'istanza della classe `AsyncBase`.

### <a name="public-methods"></a>Metodi pubblici

Nome                                         | Descrizione
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Annulla](#cancel)                 | Annulla un'operazione asincrona.
[AsyncBase::Chiudi](#close)                   | Chiude l'operazione asincrona.
[AsyncBase::FireCompletion](#firecompletion) | Richiama il gestore eventi di completamento o reimposta il delegato di stato interno.
[AsyncBase::FireProgress](#fireprogress)     | Richiama il gestore eventi di stato corrente.
[AsyncBase::get_ErrorCode](#get-errorcode)   | Recupera il codice di errore per l'operazione asincrona corrente.
[AsyncBase::get_Id](#get-id)                 | Recupera l'handle dell'operazione asincrona.
[AsyncBase::get_Status](#get-status)         | Recupera un valore che indica lo stato dell'operazione asincrona.
[AsyncBase::GetOnComplete](#getoncomplete)   | Copia l'indirizzo del gestore eventi di completamento corrente nella variabile specificata.
[AsyncBase::GetOnProgressAsyncBase::GetOnProgress](#getonprogress)   | Copia l'indirizzo del gestore dell'evento di stato corrente nella variabile specificata.
[AsyncBase::put_Id](#put-id)                 | Imposta l'handle dell'operazione asincrona.
[AsyncBase::PutOnComplete](#putoncomplete)   | Imposta l'indirizzo del gestore eventi di completamento sul valore specificato.
[AsyncBase::PutOnProgress](#putonprogress)   | Imposta l'indirizzo del gestore eventi di stato sul valore specificato.

### <a name="protected-methods"></a>Metodi protetti

Nome                                                                         | Descrizione
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Verifica se le proprietà del delegato possono essere modificate nello stato asincrono corrente.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Verifica se i risultati di un'operazione asincrona possono essere raccolti nello stato asincrono corrente.
[AsyncBase::ContinueAsyncOperationAsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Determina se l'operazione asincrona deve continuare l'elaborazione o interrompersi.
[AsyncBase::StatoCorrente](#currentstatus)                                   | Recupera lo stato dell'operazione asincrona corrente.
[AsyncBase::ErrorCode](#errorcode)                                           | Recupera il codice di errore per l'operazione asincrona corrente.
[AsyncBase::OnCancel](#oncancel)                                             | Quando sottoposto a override in una classe derivata, annulla un'operazione asincrona.
[AsyncBase::OnClose](#onclose)                                               | Quando sottoposto a override in una classe derivata, chiude un'operazione asincrona.
[AsyncBase::OnStart](#onstart)                                               | Quando sottoposto a override in una classe derivata, avvia un'operazione asincrona.
[AsyncBase::Start](#start)                                                   | Avvia l'operazione asincrona.
[AsyncBase::TryTransitionToCompleted](#trytransitiontocompleted)             | Indica se l'operazione asincrona corrente è stata completata.
[AsyncBase::TryTransitionToError](#trytransitiontoerror)                     | Indica se il codice di errore specificato può modificare lo stato di errore interno.

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Requisiti

**Intestazione:** async.h

**Spazio dei nomi:** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase::AsyncBase

Inizializza un'istanza della classe `AsyncBase`.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase::Annulla

Annulla un'operazione asincrona.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Valore restituito

Per impostazione predefinita, restituisce sempre S_OK.

### <a name="remarks"></a>Osservazioni

`Cancel()`è un'implementazione predefinita di `IAsyncInfo::Cancel`, e non esegue alcun lavoro effettivo. Per annullare effettivamente un'operazione asincrona, eseguire l'override del `OnCancel()` metodo virtuale puro.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Verifica se le proprietà del delegato possono essere modificate nello stato asincrono corrente.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Valore restituito

S_OK se le proprietà del delegato possono essere modificate; in caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Verifica se i risultati di un'operazione asincrona possono essere raccolti nello stato asincrono corrente.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Valore restituito

S_OK se i risultati possono essere raccolti; in caso contrario, E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase::Chiudi

Chiude l'operazione asincrona.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Valore restituito

S_OK se l'operazione viene chiusa o è già chiusa; in caso contrario, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Osservazioni

`Close()`è un'implementazione predefinita di `IAsyncInfo::Close`, e non esegue alcun lavoro effettivo. Per chiudere effettivamente un'operazione asincrona, eseguire l'override del `OnClose()` metodo virtuale puro.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperationAsyncBase::ContinueAsyncOperation

Determina se l'operazione asincrona deve continuare l'elaborazione o interrompersi.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Valore restituito

**true** se viene *avviato*lo stato corrente dell'operazione asincrona, ovvero l'operazione deve continuare. In caso contrario, **false**, che indica che l'operazione deve essere interrotta.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase::StatoCorrente

Recupera lo stato dell'operazione asincrona corrente.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parametri

*status*<br/>
Posizione in cui questa operazione archivia lo stato corrente.

### <a name="remarks"></a>Osservazioni

Questa operazione è thread-safe.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase::ErrorCode

Recupera il codice di errore per l'operazione asincrona corrente.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametri

*error*<br/>
Posizione in cui questa operazione archivia il codice di errore corrente.

### <a name="remarks"></a>Osservazioni

Questa operazione è thread-safe.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase::FireCompletion

Richiama il gestore eventi di completamento o reimposta il delegato di stato interno.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Osservazioni

La prima `FireCompletion()` versione di reimposta la variabile di delegato progress interna. La seconda versione richiama il gestore eventi di completamento se l'operazione asincrona è stata completata.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase::FireProgress

Richiama il gestore eventi di stato corrente.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parametri

*Arg*<br/>
Metodo del gestore eventi da richiamare.

### <a name="remarks"></a>Osservazioni

`ProgressTraits`è derivato da [ArgTraitsHelper Structure](argtraitshelper-structure.md).

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase::get_ErrorCode

Recupera il codice di errore per l'operazione asincrona corrente.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parametri

*Errorcode*<br/>
Posizione in cui è archiviato il codice di errore corrente.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_ILLEGAL_METHOD_CALL se l'operazione asincrona corrente viene chiusa.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase::get_Id

Recupera l'handle dell'operazione asincrona.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametri

*id*<br/>
Posizione in cui deve essere archiviato l'handle.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Osservazioni

Questo metodo implementa `IAsyncInfo::get_Id`.

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase::get_Status

Recupera un valore che indica lo stato dell'operazione asincrona.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametri

*status*<br/>
Posizione in cui deve essere archiviato lo stato. Per ulteriori informazioni, vedere l'enumerazione `Windows::Foundation::AsyncStatus`.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Osservazioni

Questo metodo implementa `IAsyncInfo::get_Status`.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase::GetOnComplete

Copia l'indirizzo del gestore eventi di completamento corrente nella variabile specificata.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parametri

*completeHandler (completa)*<br/>
Posizione in cui è archiviato l'indirizzo del gestore eventi di completamento corrente.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase::GetOnProgressAsyncBase::GetOnProgress

Copia l'indirizzo del gestore dell'evento di stato corrente nella variabile specificata.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parametri

*progressHandler (gestore progredi*<br/>
Posizione in cui è archiviato l'indirizzo del gestore dell'evento di stato corrente.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase::OnCancel

Quando sottoposto a override in una classe derivata, annulla un'operazione asincrona.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase::OnClose

Quando sottoposto a override in una classe derivata, chiude un'operazione asincrona.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase::OnStart

Quando sottoposto a override in una classe derivata, avvia un'operazione asincrona.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase::put_Id

Imposta l'handle dell'operazione asincrona.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parametri

*id*<br/>
Handle diverso da zero.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_INVALIDARG o E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase::PutOnComplete

Imposta l'indirizzo del gestore eventi di completamento sul valore specificato.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametri

*completeHandler (completa)*<br/>
Indirizzo su cui è impostato il gestore eventi di completamento.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase::PutOnProgress

Imposta l'indirizzo del gestore eventi di stato sul valore specificato.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parametri

*progressHandler (gestore progredi*<br/>
Indirizzo su cui è impostato il gestore eventi di stato.

### <a name="return-value"></a>Valore restituito

S_OK in caso di esito positivo; in caso contrario, E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase::Start

Avvia l'operazione asincrona.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Valore restituito

S_OK se l'operazione viene avviata o già avviata; in caso contrario, E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Osservazioni

`Start()`è un metodo protetto che non è visibile esternamente perché le operazioni asincrone "avvio a caldo" prima di restituire al chiamante.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToCompleted

Indica se l'operazione asincrona corrente è stata completata.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Valore restituito

**true** se l'operazione asincrona è stata completata; in caso contrario, **false**.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase::TryTransitionToError

Indica se il codice di errore specificato può modificare lo stato di errore interno.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametri

*error*<br/>
Un HRESULT di errore.

### <a name="return-value"></a>Valore restituito

**true** se lo stato di errore interno è stato modificato; in caso contrario, **false**.

### <a name="remarks"></a>Osservazioni

Questa operazione modifica lo stato di errore solo se lo stato di errore è già impostato su S_OK. Questa operazione non ha effetto se lo stato di errore è già errore, annullato, completato o chiuso.
