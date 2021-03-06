---
title: Classe task_continuation_context
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142581"
---
# <a name="task_continuation_context-class"></a>Classe task_continuation_context

La classe `task_continuation_context` consente di specificare dove eseguire una continuazione. È utile usare questa classe solo da un'app Windows Runtime. Per le app non Windows Runtime, il contesto di esecuzione della continuazione dell'attività è determinato dal runtime e non è configurabile.

## <a name="syntax"></a>Sintassi

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|Restituisce un oggetto contesto di continuazione dell'attività che rappresenta il contesto del thread WinRT corrente.|
|[use_arbitrary](#use_arbitrary)|Crea un contesto di continuazione delle attività che consente al runtime di scegliere il contesto di esecuzione per una continuazione.|
|[use_current](#use_current)|Restituisce un oggetto del contesto di continuazione di attività che rappresenta il contesto di esecuzione corrente.|
|[use_default](#use_default)|Crea il contesto di continuazione di attività predefinito.|
|[use_synchronous_execution](#use_synchronous_execution)|Restituisce un oggetto di contesto di continuazione dell'attività che rappresenta il contesto di esecuzione sincrona.|

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>Requisiti

**Intestazione:** ppltasks. h

**Spazio dei nomi:** Concurrency

## <a name="get_current_winrt_context"></a>get_current_winrt_context

Restituisce un oggetto contesto di continuazione dell'attività che rappresenta il contesto del thread WinRT corrente.

### <a name="syntax"></a>Sintassi

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>Valore restituito

Contesto del thread del Windows Runtime corrente. Restituisce un task_continuation_context vuoto se chiamato da un contesto non Windows Runtime.

### <a name="remarks"></a>Osservazioni

Il metodo `get_current_winrt_context` acquisisce il contesto del thread Windows Runtime del chiamante. Restituisce un contesto vuoto ai chiamanti non Windows Runtime.

Il valore restituito da `get_current_winrt_context` può essere utilizzato per indicare al runtime che la continuazione deve essere eseguita nel modello di Apartment del contesto acquisito (STA vs MTA), indipendentemente dal fatto che l'attività precedente sia compatibile con l'Apartment. Un'attività compatibile con l'Apartment è un'attività che esegue l'unwrapping di un'interfaccia di `IAsyncInfo` Windows Runtime o un'attività discendente da tale attività.

Questo metodo è simile al metodo `use_current`, ma è disponibile anche per il codice nativo C++ senza C++supporto dell'estensione/CX. È progettato per essere usato dagli utenti avanzati che C++scrivono il codice della libreria/CX-Agnostic per i chiamanti sia nativi che Windows Runtime. A meno che questa funzionalità non sia necessaria, è consigliabile usare il metodo `use_current`, disponibile solo C++per i client/CX.

## <a name="use_arbitrary"></a>use_arbitrary

Crea un contesto di continuazione delle attività che consente al runtime di scegliere il contesto di esecuzione per una continuazione.

### <a name="syntax"></a>Sintassi

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>Valore restituito

Contesto di continuazione di attività che rappresenta una posizione arbitraria.

### <a name="remarks"></a>Osservazioni

Quando viene utilizzato questo contesto di continuazione, la continuazione verrà eseguita in un contesto scelto dal runtime anche se l'attività precedente è compatibile con l'Apartment.

`use_arbitrary` può essere usato per disattivare il comportamento predefinito per una continuazione in un'attività in grado di riconoscere Apartment creata in un STA.

Questo metodo è disponibile solo per le app Windows Runtime.

## <a name="use_current"></a>use_current

Restituisce un oggetto del contesto di continuazione di attività che rappresenta il contesto di esecuzione corrente.

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>Valore restituito

Contesto di esecuzione corrente.

### <a name="remarks"></a>Osservazioni

Questo metodo acquisisce il contesto di Windows Runtime del chiamante in modo che sia possibile eseguire le continuazioni nell'Apartment a destra.

Il valore restituito da `use_current` può essere utilizzato per indicare al runtime che la continuazione deve essere eseguita nel contesto acquisito (STA e MTA) indipendentemente dal fatto che l'attività precedente sia o meno compatibile con l'Apartment. Un'attività compatibile con l'Apartment è un'attività che esegue l'unwrapping di un'interfaccia di `IAsyncInfo` Windows Runtime o un'attività discendente da tale attività.

Questo metodo è disponibile solo per le app Windows Runtime.

## <a name="use_default"></a>use_default

Crea il contesto di continuazione di attività predefinito.

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>Valore restituito

Contesto di continuazione predefinito.

### <a name="remarks"></a>Osservazioni

Il contesto predefinito viene usato se non si specifica un contesto di continuazione quando si chiama il metodo `then`. Nelle applicazioni Windows per Windows 7 e versioni precedenti, nonché applicazioni desktop in Windows 8 e versioni successive, il runtime determina la posizione in cui verranno eseguite le continuazioni delle attività. Tuttavia, in un'app Windows Runtime, il contesto di continuazione predefinito per una continuazione in un'attività compatibile con l'Apartment è l'Apartment in cui viene richiamato `then`.

Un'attività compatibile con l'Apartment è un'attività che esegue l'unwrapping di un'interfaccia di `IAsyncInfo` Windows Runtime o un'attività discendente da tale attività. Se pertanto si pianifica una continuazione su un'attività in grado di riconoscere un Apartment in un Windows Runtime STA, la continuazione verrà eseguita in tale STA.

Una continuazione su un'attività non compatibile con l'Apartment verrà eseguita in un contesto scelto dal runtime.

## <a name="use_synchronous_execution"></a>task_continuation_context:: use_synchronous_execution

Restituisce un oggetto di contesto di continuazione dell'attività che rappresenta il contesto di esecuzione sincrona.

### <a name="syntax"></a>Sintassi

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>Valore restituito

Contesto di esecuzione sincrona.

### <a name="remarks"></a>Osservazioni

Il metodo `use_synchronous_execution` impone l'esecuzione sincrona dell'attività di continuazione sul contesto, causando il completamento dell'attività precedente.

Se l'attività precedente è già stata completata quando viene collegata la continuazione, la continuazione viene eseguita in modo sincrono nel contesto che collega la continuazione.

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi concurrency](concurrency-namespace.md)
