---
title: Classe future
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: e71c750ddeb198faa3ae9c5960b2668c376241ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370711"
---
# <a name="future-class"></a>Classe future

Descrive un *oggetto restituito asincrono*.

## <a name="syntax"></a>Sintassi

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Osservazioni

Ogni *provider asincrono* standard restituisce un oggetto il cui tipo è una creazione di un'istanza del modello. Un oggetto `future` fornisce l'unico accesso al provider asincrono a cui è associato. Se sono necessari più oggetti restituiti asincroni associati allo stesso provider asincrono, copiare l'oggetto `future` in un oggetto [shared_future](../standard-library/shared-future-class.md).

## <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[Futuro](#future)|Costruisce un oggetto `future`.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[get](#get)|Recupera il risultato archiviato nello stato asincrono associato.|
|[condividi](#share)|Converte l'oggetto in `shared_future`.|
|[Valido](#valid)|Specifica se l'oggetto non è vuoto.|
|[Aspettare](#wait)|Blocca il thread corrente finché lo stato asincrono associato non è ready.|
|[wait_for](#wait_for)|Blocca finché lo stato asincrono associato non è ready o finché non trascorre il periodo di tempo specificato.|
|[wait_until](#wait_until)|Blocca finché lo stato asincrono associato non è ready o fino al momento specificato.|

### <a name="public-operators"></a>Operatori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[future::operator=](#op_eq)|Trasferisce lo stato asincrono associato da un oggetto specificato.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<> futuri

**Spazio dei nomi:** std

## <a name="futurefuture-constructor"></a><a name="future"></a>Costruttore future::future

Costruisce un oggetto `future`.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parametri

*Altro*\
Oggetto `future` .

### <a name="remarks"></a>Osservazioni

Il primo costruttore crea un oggetto `future` che non ha uno stato asincrono associato.

Il secondo costruttore `future` costruisce un oggetto e trasferisce lo stato asincrono associato da *Other*. *Other* non ha più uno stato asincrono associato.

## <a name="futureget"></a><a name="get"></a>futuro::ottenere

Recupera il risultato archiviato nello stato asincrono associato.

```cpp
Ty get();
```

### <a name="return-value"></a>Valore restituito

Se il risultato è un'eccezione, il metodo la genera nuovamente. In caso contrario, viene restituito il risultato.

### <a name="remarks"></a>Osservazioni

Prima di recuperare il risultato, questo metodo blocca il thread corrente finché lo stato asincrono associato non è ready.

Per la specializzazione parziale `future<Ty&>`, il valore archiviato è di fatto un riferimento all'oggetto passato al provider asincrono come valore restituito.

Poiché non esiste alcun `future<void>`valore archiviato per la specializzazione , il metodo restituisce **void**.

In altre specializzazioni il metodo sposta il relativo valore restituito dal valore archiviato. Pertanto, chiamare questo metodo solo una volta.

## <a name="futureoperator"></a><a name="op_eq"></a>futuro::operatore

Trasferisce uno stato asincrono associato da un oggetto specificato.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parametri

*va bene*\
Oggetto `future` .

### <a name="return-value"></a>Valore restituito

`*this`

### <a name="remarks"></a>Osservazioni

Dopo il trasferimento, *Right* non ha più uno stato asincrono associato.

## <a name="futureshare"></a><a name="share"></a>futuro::condividere

Converte l'oggetto in un oggetto [shared_future](../standard-library/shared-future-class.md).

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Valore restituito

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>futuro::valido

Specifica se l'oggetto ha uno stato asincrono associato.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valore restituito

**true** se all'oggetto è associato uno stato asincrono; in caso contrario, **false**.

## <a name="futurewait"></a><a name="wait"></a>futuro::attendere

Blocca il thread corrente finché lo stato asincrono associato non è *ready*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Osservazioni

Uno stato asincrono associato è *pronto* solo se il provider asincrono ha archiviato un valore restituito o archiviato un'eccezione.

## <a name="futurewait_for"></a><a name="wait_for"></a>futuro::wait_for

Blocca il thread corrente finché lo stato asincrono associato non è *ready* o finché non trascorre un determinato intervallo di tempo.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametri

*Rel_time*\
Oggetto [chrono::duration](../standard-library/duration-class.md) che specifica un intervallo di tempo massimo per il blocco del thread.

### <a name="return-value"></a>Valore restituito

Oggetto [future_status](../standard-library/future-enums.md#future_status) che indica il motivo della restituzione.

### <a name="remarks"></a>Osservazioni

Lo stato asincrono associato è ready solo se il relativo provider asincrono ha archiviato un valore restituito o un'eccezione.

## <a name="futurewait_until"></a><a name="wait_until"></a>future::wait_until

Blocca il thread corrente finché lo stato asincrono associato non è *ready* o fino a un determinato momento.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametri

*Abs_time*\
Oggetto [chrono::time_point](../standard-library/time-point-class.md) che specifica un momento dopo il quale il thread può essere sbloccato.

### <a name="return-value"></a>Valore restituito

Oggetto [future_status](../standard-library/future-enums.md#future_status) che indica il motivo della restituzione.

### <a name="remarks"></a>Osservazioni

Uno stato asincrono associato è *pronto* solo se il provider asincrono ha archiviato un valore restituito o archiviato un'eccezione.

## <a name="see-also"></a>Vedere anche

[Riferimento ai file di intestazione](../standard-library/cpp-standard-library-header-files.md)\
[\<>futuro](../standard-library/future.md)
