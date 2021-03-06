---
title: Classe AgileEventSource
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
helpviewer_keywords:
- AgileEventSource class
ms.openlocfilehash: 71a70f783d8f8967d755bb788f4aae4861340d64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214188"
---
# <a name="agileeventsource-class"></a>Classe AgileEventSource

Rappresenta un evento generato da un componente agile, ovvero un componente a cui è possibile accedere da qualsiasi thread. Eredita da [EventSource](eventsource-class.md) ed esegue l'override della funzione membro `Add` con un parametro di tipo aggiuntivo per specificare le opzioni per la modalità di richiamo dell'evento agile.

## <a name="syntax"></a>Sintassi

```cpp
template<
    typename TDelegateInterface,
    typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>
>
class AgileEventSource :
    public Microsoft::WRL::EventSource<
        TDelegateInterface, TEventSourceOptions>;
```

## <a name="parameters"></a>Parametri

*TDelegateInterface*<br/>
Interfaccia per un delegato che rappresenta un gestore eventi.

*TEventSourceOptions*<br/>
Struttura [InvokeModeOptions](invokemodeoptions-structure.md) il cui campo invokeMode è impostato su `InvokeMode::StopOnFirstError` o `InvokeMode::FireAll`.

## <a name="remarks"></a>Osservazioni

La maggior parte dei componenti del Windows Runtime sono componenti agile. Per ulteriori informazioni, vedere [Threading e marshalling (C++/CX)](../../cppcx/threading-and-marshaling-c-cx.md).

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`EventSource`

`AgileEventSource`

## <a name="requirements"></a>Requisiti

**Intestazione:** Event. h

**Spazio dei nomi:** Microsoft::WRL

## <a name="members"></a>Members

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[Metodo AgileEventSource:: Add](#add)|Accoda il gestore eventi agile rappresentato dall'interfaccia del delegato specificata al set di gestori eventi per l'oggetto **AgileEventSource** corrente.|

## <a name="agileeventsourceadd-method"></a><a name="add"></a>Metodo AgileEventSource:: Add

Accoda il gestore eventi rappresentato dall'interfaccia del delegato specificata al set di gestori eventi per l'oggetto [EventSource](eventsource-class.md) corrente.

### <a name="syntax"></a>Sintassi

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>Parametri

*delegateInterface*<br/>
Interfaccia per un oggetto delegato, che rappresenta un gestore eventi.

*token*<br/>
Al termine di questa operazione, un handle che rappresenta l'evento. Utilizzare questo token come parametro per il metodo `Remove()` per rimuovere il gestore eventi.

### <a name="return-value"></a>Valore restituito

S_OK se riesce; in caso contrario, HRESULT indica un errore.

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi Microsoft::WRL](microsoft-wrl-namespace.md)
