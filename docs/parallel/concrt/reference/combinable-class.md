---
title: Classe combinable
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: a1954cd3a69233deed053da5b5fdef0dbc183b80
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141438"
---
# <a name="combinable-class"></a>Classe combinable

L'oggetto `combinable<T>` ha lo scopo di fornire copie di dati di thread privato, per eseguire calcoli secondari locali per thread senza blocco durante algoritmi paralleli. Alla fine dell'operazione parallela, è possibile unire i sub-calcoli del thread privato in un risultato finale. Questa classe può essere usata in sostituzione di una variabile condivisa e può determinare un miglioramento delle prestazioni qualora vi fosse invece molto conflitto su tale variabile condivisa.

## <a name="syntax"></a>Sintassi

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>Parametri

*T*<br/>
Tipo di dati del risultato Unito finale. Il tipo deve avere un costruttore di copia e un costruttore predefinito.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Costruttori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[combinable](#ctor)|Di overload. Costruisce un oggetto `combinable` nuovo.|
|[~ distruttore combinabile](#dtor)|Elimina un oggetto `combinable`.|

### <a name="public-methods"></a>Metodi pubblici

|Nome|Descrizione|
|----------|-----------------|
|[deselezionare](#clear)|Cancella tutti i risultati di calcolo intermedi da un utilizzo precedente.|
|[combine](#combine)|Calcola un valore finale dal set di sottocalcoli locali del thread chiamando il functor combinato fornito.|
|[combine_each](#combine_each)|Calcola un valore finale dal set di sottocalcoli locali del thread chiamando il functor di combinazione fornito una volta per ogni sottocalcolo locale del thread. Il risultato finale viene accumulato dall'oggetto funzione.|
|[local](#local)|Di overload. Restituisce un riferimento al sottocalcolo thread-privato.|

### <a name="public-operators"></a>Operatori pubblici

|Nome|Descrizione|
|----------|-----------------|
|[operator=](#operator_eq)|Assegna a un oggetto `combinable` da un altro oggetto `combinable`.|

## <a name="remarks"></a>Osservazioni

Per altre informazioni, vedere [contenitori e oggetti paralleli](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`combinable`

## <a name="requirements"></a>Requisiti

**Intestazione:** ppl. h

**Spazio dei nomi:** Concurrency

## <a name="clear"></a>deselezionare

Cancella tutti i risultati di calcolo intermedi da un utilizzo precedente.

```cpp
void clear();
```

## <a name="ctor"></a>combinable

Costruisce un oggetto `combinable` nuovo.

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parametri

*_Function*<br/>
Tipo dell'oggetto functor di inizializzazione.

*_FnInitialize*<br/>
Funzione che verrà chiamata per inizializzare ogni nuovo valore thread-private del tipo `T`. Deve supportare un operatore di chiamata di funzione con la firma `T ()`.

*_Copy*<br/>
Oggetto `combinable` esistente da copiare in questo oggetto.

### <a name="remarks"></a>Osservazioni

Il primo costruttore inizializza nuovi elementi con il costruttore predefinito per il tipo `T`.

Il secondo costruttore inizializza nuovi elementi utilizzando il functor di inizializzazione fornito come parametro `_FnInitialize`.

Il terzo costruttore è il costruttore di copia.

## <a name="dtor"></a>~ combinable

Elimina un oggetto `combinable`.

```cpp
~combinable();
```

## <a name="combine"></a>combinare

Calcola un valore finale dal set di sottocalcoli locali del thread chiamando il functor combinato fornito.

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametri

*_Function*<br/>
Tipo dell'oggetto funzione che verrà richiamato per combinare due calcoli secondari locali del thread.

*_FnCombine*<br/>
Functor usato per combinare i sottocalcoli. La firma è `T (T, T)` o `T (const T&, const T&)`e deve essere associativa e commutativa.

### <a name="return-value"></a>Valore restituito

Risultato finale della combinazione di tutti i calcoli secondari thread-privati.

## <a name="combine_each"></a>combine_each

Calcola un valore finale dal set di sottocalcoli locali del thread chiamando il functor di combinazione fornito una volta per ogni sottocalcolo locale del thread. Il risultato finale viene accumulato dall'oggetto funzione.

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametri

*_Function*<br/>
Tipo dell'oggetto funzione che verrà richiamato per combinare un sottocalcolo locale a thread singolo.

*_FnCombine*<br/>
Il functor usato per combinare un calcolo secondario. La firma è `void (T)` o `void (const T&)`e deve essere associativa e commutativa.

## <a name="local"></a>locale

Restituisce un riferimento al sottocalcolo thread-privato.

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parametri

*_Exists*<br/>
Riferimento a un valore booleano. Il valore booleano a cui fa riferimento questo argomento verrà impostato su **true** se il sottocalcolo esiste già nel thread e impostato su **false** se si tratta del primo sottocalcolo di questo thread.

### <a name="return-value"></a>Valore restituito

Riferimento al sottocalcolo thread-privato.

## <a name="operator_eq"></a>operatore =

Assegna a un oggetto `combinable` da un altro oggetto `combinable`.

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parametri

*_Copy*<br/>
Oggetto `combinable` esistente da copiare in questo oggetto.

### <a name="return-value"></a>Valore restituito

Riferimento a questo oggetto `combinable`.

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi concurrency](concurrency-namespace.md)
