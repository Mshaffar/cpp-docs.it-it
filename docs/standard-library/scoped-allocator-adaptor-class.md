---
title: Classe scoped_allocator_adaptor
ms.date: 11/04/2016
f1_keywords:
- scoped_allocator/std::scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor::rebind Struct
- scoped_allocator/std::scoped_allocator_adaptor::allocate
- scoped_allocator/std::scoped_allocator_adaptor::construct
- scoped_allocator/std::scoped_allocator_adaptor::deallocate
- scoped_allocator/std::scoped_allocator_adaptor::destroy
- scoped_allocator/std::scoped_allocator_adaptor::inner_allocator
- scoped_allocator/std::scoped_allocator_adaptor::max_size
- scoped_allocator/std::scoped_allocator_adaptor::outer_allocator
- scoped_allocator/std::scoped_allocator_adaptor::select_on_container_copy_construction
helpviewer_keywords:
- std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor::allocate
- std::scoped_allocator_adaptor::construct
- std::scoped_allocator_adaptor::deallocate
- std::scoped_allocator_adaptor::destroy
- std::scoped_allocator_adaptor::inner_allocator
- std::scoped_allocator_adaptor::max_size
- std::scoped_allocator_adaptor::outer_allocator
- std::scoped_allocator_adaptor::select_on_container_copy_construction
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
ms.openlocfilehash: b08cf1858cb0f9bf4dc6201edc2502d48754ff77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373392"
---
# <a name="scoped_allocator_adaptor-class"></a>Classe scoped_allocator_adaptor

Rappresenta un annidamento di allocatori.

## <a name="syntax"></a>Sintassi

```cpp
template <class Outer, class... Inner>
class scoped_allocator_adaptor;
```

## <a name="remarks"></a>Osservazioni

Il modello di classe incapsula un nido di uno o più allocatori. Ogni classe di questo tipo ha un allocatore più esterno di tipo `outer_allocator_type`, un sinonimo di `Outer`, che è una base pubblica dell'oggetto `scoped_allocator_adaptor`. `Outer` viene usato per allocare memoria da destinare a un contenitore. È possibile ottenere un riferimento a questo oggetto allocatore di base chiamando `outer_allocator`.

La parte rimanente dell'annidamento è di tipo `inner_allocator_type`. Per allocare memoria per gli elementi all'interno di un contenitore viene usato un allocatore interno. È possibile ottenere un riferimento all'oggetto archiviato di questo tipo chiamando `inner_allocator`. Se `Inner...` non è vuoto, `inner_allocator_type` è di tipo `scoped_allocator_adaptor<Inner...>` e `inner_allocator` definisce un oggetto membro. In caso contrario, `inner_allocator_type` è di tipo `scoped_allocator_adaptor<Outer>` e `inner_allocator` definisce l'intero oggetto.

L'annidamento si comporta come se avesse una profondità arbitraria, replicando l'allocatore incapsulato più interno in base alle esigenze.

Diversi concetti che non fanno parte dell'interfaccia visibile aiutano a descrivere il comportamento di questo modello di classe. Un *allocatore più esterno* svolge una funzione di mediazione per tutte le chiamate ai metodi construct e destroy. È definito dalla funzione ricorsiva `OUTERMOST(X)`, dove `OUTERMOST(X)` ha uno dei valori seguenti:

- Se `X.outer_allocator()` è nel formato corretto, `OUTERMOST(X)` è `OUTERMOST(X.outer_allocator())`.

- In caso contrario, `OUTERMOST(X)` sarà `X`.

Tre tipi sono definiti a scopo di illustrazione:

|Type|Descrizione|
|----------|-----------------|
|`Outermost`|Tipo di `OUTERMOST(*this)`.|
|`Outermost_traits`|`allocator_traits<Outermost>`|
|`Outer_traits`|`allocator_traits<Outer>`|

### <a name="constructors"></a>Costruttori

|Nome|Descrizione|
|----------|-----------------|
|[scoped_allocator_adaptor](#scoped_allocator_adaptor)|Costruisce un oggetto `scoped_allocator_adaptor`.|

### <a name="typedefs"></a>Typedef

|Nome|Descrizione|
|----------|-----------------|
|`const_pointer`|Questo tipo è un sinonimo del tipo `const_pointer` associato all'allocatore `Outer`.|
|`const_void_pointer`|Questo tipo è un sinonimo del tipo `const_void_pointer` associato all'allocatore `Outer`.|
|`difference_type`|Questo tipo è un sinonimo del tipo `difference_type` associato all'allocatore `Outer`.|
|`inner_allocator_type`|Questo tipo è un sinonimo del tipo dell'adattatore annidato `scoped_allocator_adaptor<Inner...>`.|
|`outer_allocator_type`|Questo tipo è un sinonimo del tipo dell'allocatore di base `Outer`.|
|`pointer`|Questo tipo è un sinonimo del tipo `pointer` associato all'allocatore `Outer`.|
|`propagate_on_container_copy_assignment`|Il tipo contiene true solo se `Outer_traits::propagate_on_container_copy_assignment` o `inner_allocator_type::propagate_on_container_copy_assignment` contiene true.|
|`propagate_on_container_move_assignment`|Il tipo contiene true solo se `Outer_traits::propagate_on_container_move_assignment` o `inner_allocator_type::propagate_on_container_move_assignment` contiene true.|
|`propagate_on_container_swap`|Il tipo contiene true solo se `Outer_traits::propagate_on_container_swap` o `inner_allocator_type::propagate_on_container_swap` contiene true.|
|`size_type`|Questo tipo è un sinonimo del tipo `size_type` associato all'allocatore `Outer`.|
|`value_type`|Questo tipo è un sinonimo del tipo `value_type` associato all'allocatore `Outer`.|
|`void_pointer`|Questo tipo è un sinonimo del tipo `void_pointer` associato all'allocatore `Outer`.|

### <a name="structs"></a>Struct

|Nome|Descrizione|
|----------|-----------------|
|[scoped_allocator_adaptor:rebind Struct](#rebind_struct)|Definisce il tipo `Outer::rebind\<Other>::other` come sinonimo di `scoped_allocator_adaptor\<Other, Inner...>`.|

### <a name="methods"></a>Metodi

|Nome|Descrizione|
|----------|-----------------|
|[Allocare](#allocate)|Alloca memoria tramite l'allocatore `Outer`.|
|[costrutto](#construct)|Costruisce un oggetto.|
|[Deallocare](#deallocate)|Dealloca oggetti usando l'allocatore esterno.|
|[Distruggere](#destroy)|Distrugge un oggetto specificato.|
|[inner_allocator](#inner_allocator)|Recupera un riferimento all'oggetto archiviato di tipo `inner_allocator_type`.|
|[max_size](#max_size)|Determina il numero massimo di oggetti che possono essere allocati dall'allocatore esterno.|
|[outer_allocator](#outer_allocator)|Recupera un riferimento all'oggetto archiviato di tipo `outer_allocator_type`.|
|[select_on_container_copy_construction](#select_on_container_copy_construction)|Crea un nuovo oggetto `scoped_allocator_adaptor` con ogni oggetto allocatore archiviato inizializzato tramite una chiamata a `select_on_container_copy_construction` per ogni allocatore corrispondente.|

### <a name="operators"></a>Operatori

|Operatore|Descrizione|
|-|-|
|[operatore di comando](#op_as)||
|[operatore di comando](#op_eq_eq)||
|[operatore!](#op_noeq)||

## <a name="requirements"></a>Requisiti

**Intestazione:** \<scoped_allocator>

**Spazio dei nomi:** std

## <a name="scoped_allocator_adaptorallocate"></a><a name="allocate"></a>scoped_allocator_adaptor::allocare

Alloca memoria tramite l'allocatore `Outer`.

```cpp
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```

### <a name="parameters"></a>Parametri

*Conteggio*\
Numero di elementi per cui deve essere allocata memoria sufficiente.

*Suggerimento*\
Puntatore che può essere utile all'oggetto allocatore individuando l'indirizzo di un oggetto allocato prima della richiesta.

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce `Outer_traits::allocate(outer_allocator(), count)`. La seconda funzione membro restituisce `Outer_traits::allocate(outer_allocator(), count, hint)`.

## <a name="scoped_allocator_adaptorconstruct"></a><a name="construct"></a>scoped_allocator_adaptor::costrutto

Costruisce un oggetto.

```cpp
template <class Ty, class... Atypes>
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,
    tuple<Atypes1&&...>
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr,
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```

### <a name="parameters"></a>Parametri

*Ptr*\
Puntatore alla posizione di memoria in cui deve essere costruito l'oggetto.

*Args*\
Elenco di argomenti.

*Prima*\
Oggetto del primo tipo in una coppia.

*Secondo*\
Oggetto del secondo tipo in una coppia.

*va bene*\
Oggetto esistente da spostare o copiare.

### <a name="remarks"></a>Osservazioni

Il primo metodo costruisce l'oggetto `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`in `xargs...` corrispondenza *di ptr* chiamando , dove è uno dei seguenti.

- Se `uses_allocator<Ty, inner_allocator_type>` contiene false, `xargs...` è `args...`.

- Se `uses_allocator<Ty, inner_allocator_type>` e `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` contengono entrambi true, `xargs...` è `allocator_arg, inner_allocator(), args...`.

- Se `uses_allocator<Ty, inner_allocator_type>` e `is_constructible<Ty, args..., inner_allocator()>` contengono entrambi true, `xargs...` è `args..., inner_allocator()`.

Il secondo metodo costruisce l'oggetto `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`coppia `xargs...` in `first...` corrispondenza di *ptr* chiamando , dove viene modificato come nell'elenco precedente e `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, dove `xargs...` viene `second...` modificato come nell'elenco precedente.

Il terzo metodo si comporta come `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.

Il quarto metodo si comporta come `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.

Il quinto metodo si comporta come `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.

Il sesto metodo si comporta come `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.

## <a name="scoped_allocator_adaptordeallocate"></a><a name="deallocate"></a>scoped_allocator_adaptor::deallocare

Dealloca oggetti usando l'allocatore esterno.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametri

*Ptr*\
Puntatore alla posizione iniziale degli oggetti da deallocare.

*Conteggio*\
Numero di oggetti da deallocare.

## <a name="scoped_allocator_adaptordestroy"></a><a name="destroy"></a>scoped_allocator_adaptor::destroy

Distrugge un oggetto specificato.

```cpp
template <class Ty>
void destroy(Ty* ptr)
```

### <a name="parameters"></a>Parametri

*Ptr*\
Puntatore all'oggetto da distruggere.

### <a name="return-value"></a>Valore restituito

`Outermost_traits::destroy(OUTERMOST(*this), ptr)`

## <a name="scoped_allocator_adaptorinner_allocator"></a><a name="inner_allocator"></a>scoped_allocator_adaptor::inner_allocator

Recupera un riferimento all'oggetto archiviato di tipo `inner_allocator_type`.

```cpp
inner_allocator_type& inner_allocator() noexcept;
const inner_allocator_type& inner_allocator() const noexcept;
```

### <a name="return-value"></a>Valore restituito

Riferimento all'oggetto archiviato di tipo `inner_allocator_type`.

## <a name="scoped_allocator_adaptormax_size"></a><a name="max_size"></a>scoped_allocator_adaptor::max_size

Determina il numero massimo di oggetti che possono essere allocati dall'allocatore esterno.

```cpp
size_type max_size();
```

### <a name="return-value"></a>Valore restituito

`Outer_traits::max_size(outer_allocator())`

## <a name="a-nameop_as--scoped_allocator_adaptoroperator"></a><a name="op_as">scoped_allocator_adaptor::operatore

```cpp
scoped_allocator_adaptor& operator=(const scoped_allocator_adaptor&) = default;
scoped_allocator_adaptor& operator=(scoped_allocator_adaptor&&) = default;
```

## <a name="a-nameop_eq_eq--scoped_allocator_adaptoroperator"></a><a name="op_eq_eq">scoped_allocator_adaptor::operatore

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator==(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="a-nameop_noeq--scoped_allocator_adaptoroperator"></a><a name="op_noeq">scoped_allocator_adaptor::operator!

```cpp
template <class OuterA1, class OuterA2, class... InnerAllocs>
bool operator!=(const scoped_allocator_adaptor<OuterA1, InnerAllocs...>& a,
const scoped_allocator_adaptor<OuterA2, InnerAllocs...>& b) noexcept;
```

## <a name="scoped_allocator_adaptorouter_allocator"></a><a name="outer_allocator"></a>scoped_allocator_adaptor::outer_allocator

Recupera un riferimento all'oggetto archiviato di tipo `outer_allocator_type`.

```cpp
outer_allocator_type& outer_allocator() noexcept;
const outer_allocator_type& outer_allocator() const noexcept;
```

### <a name="return-value"></a>Valore restituito

Riferimento all'oggetto archiviato di tipo `outer_allocator_type`.

## <a name="scoped_allocator_adaptorrebind-struct"></a><a name="rebind_struct"></a>scoped_allocator_adaptor:rebind Struct

Definisce il tipo `Outer::rebind\<Other>::other` come sinonimo di `scoped_allocator_adaptor\<Other, Inner...>`.

struct rebind Other_traits::rebind\<Altri> Other_alloc;\<typedef scoped_allocator_adaptor Other_alloc, Inner...> altro;

## <a name="scoped_allocator_adaptorscoped_allocator_adaptor-constructor"></a><a name="scoped_allocator_adaptor"></a>Costruttore scoped_allocator_adaptor::scoped_allocator_adaptor

Costruisce un oggetto `scoped_allocator_adaptor`. Include anche un distruttore.

```cpp
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(
scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;
template <class Outer2>
scoped_allocator_adaptor(Outer2&& al,
    const Inner&... rest) noexcept;

~scoped_allocator_adaptor();
```

### <a name="parameters"></a>Parametri

*va bene*\
Oggetto `scoped_allocator_adaptor` esistente.

*al*\
Allocatore esistente da usare come allocatore esterno.

*Resto*\
Elenco di allocatori da usare come allocatori interni.

### <a name="remarks"></a>Osservazioni

Il primo costruttore crea per impostazione predefinita i relativi oggetti allocator archiviati. Ognuno dei tre costruttori successivi costruisce gli oggetti allocatore archiviati dagli oggetti corrispondenti in *right*. L'ultimo costruttore crea i relativi oggetti allocator archiviati in base agli argomenti corrispondenti nell'elenco degli argomenti.

## <a name="scoped_allocator_adaptorselect_on_container_copy_construction"></a><a name="select_on_container_copy_construction"></a>scoped_allocator_adaptor::select_on_container_copy_construction

Crea un nuovo oggetto `scoped_allocator_adaptor` con ogni oggetto allocatore archiviato inizializzato tramite una chiamata a `select_on_container_copy_construction` per ogni allocatore corrispondente.

```cpp
scoped_allocator_adaptor select_on_container_copy_construction();
```

### <a name="return-value"></a>Valore restituito

Questo metodo restituisce `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. Il risultato `scoped_allocator_adaptor` è un nuovo oggetto con ogni `al.select_on_container_copy_construction()` oggetto allocatore archiviato inizializzato chiamando l'allocatore *al*.

## <a name="see-also"></a>Vedere anche

[Riferimento file di intestazione](../standard-library/cpp-standard-library-header-files.md)
