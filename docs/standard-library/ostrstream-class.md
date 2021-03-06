---
title: Classe ostrstream
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: b52ba70607a5214a6aa28f04cdded0b19a56b2f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373537"
---
# <a name="ostrstream-class"></a>Classe ostrstream

Descrive un oggetto che controlla l'inserimento di elementi e oggetti codificati in un buffer del flusso della classe [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Sintassi

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Osservazioni

L'oggetto archivia un oggetto della classe `strstreambuf`.

> [!NOTE]
> Questa classe è deprecata. Provare a usare [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) o [wostringstream](../standard-library/sstream-typedefs.md#wostringstream).

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[ostrstream](#ostrstream)|Costruisce un oggetto di tipo `ostrstream`.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[Congelare](#freeze)|Fa sì che un buffer del flusso non sia disponibile tramite le operazioni di buffer del flusso.|
|[pcount](#pcount)|Restituisce un conteggio del numero di elementi scritti nella sequenza controllata.|
|[rdbuf](#rdbuf)|Restituisce un puntatore all'oggetto `strstreambuf` associato del flusso.|
|[Str](#str)|Chiama [freeze](../standard-library/strstreambuf-class.md#freeze) e quindi restituisce un puntatore all'inizio della sequenza controllata.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<strstream>

**Spazio dei nomi:** std

## <a name="ostrstreamfreeze"></a><a name="freeze"></a>ostrstream::congelamento

Fa sì che un buffer del flusso non sia disponibile tramite le operazioni di buffer del flusso.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parametri

*_Freezeit*\
Oggetto **bool** che indica se si desidera che il flusso venga bloccato.

### <a name="remarks"></a>Osservazioni

La funzione membro chiama [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Esempio

Vedere [strstream::freeze](../standard-library/strstreambuf-class.md#freeze) per un `freeze`esempio che utilizza .

## <a name="ostrstreamostrstream"></a><a name="ostrstream"></a>ostrstream::ostrstream

Costruisce un oggetto di tipo `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parametri

*Ptr*\
Buffer.

*Conteggio*\
Dimensioni del buffer in byte.

*_Mode*\
Modalità di input e output del buffer. Per altre informazioni, vedere [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="remarks"></a>Osservazioni

Entrambi i costruttori inizializzano la classe base `sb` chiamando [ostream](../standard-library/ostream-typedefs.md#ostream)(**sb**), dove è l'oggetto archiviato della classe [strstreambuf](../standard-library/strstreambuf-class.md). Il primo costruttore `sb` viene `strstreambuf`inizializzato anche chiamando . Il secondo costruttore inizializza la classe di base in uno dei due modi seguenti:

- Se `_Mode`  &  **ios_base::app**è uguale `ptr` a 0, è `count` necessario designare il `strstreambuf``ptr`primo `count`elemento di una matrice di elementi e le chiamate al costruttore ( , , `ptr`).

- In `ptr` caso contrario, è necessario designare il primo elemento di una `ptr`matrice di elementi `strstreambuf``ptr`count `count` `ptr`  +  `strlen`che `ptr`contiene una stringa C il cui primo elemento è designato da e il costruttore chiama ( , , ( ). ).

## <a name="ostrstreampcount"></a><a name="pcount"></a>ostrstream::pcount

Restituisce un conteggio del numero di elementi scritti nella sequenza controllata.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valore restituito

Numero di elementi scritti nella sequenza controllata.

### <a name="remarks"></a>Osservazioni

La funzione membro restituisce [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Esempio

Vedere [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) per un esempio d'uso di `pcount`.

## <a name="ostrstreamrdbuf"></a><a name="rdbuf"></a>ostrstream::rdbuf

Restituisce un puntatore all'oggetto strstreambuf associato del flusso.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valore restituito

Puntatore all'oggetto strstreambuf associato del flusso.

### <a name="remarks"></a>Osservazioni

La funzione membro restituisce l'indirizzo `pointer` del buffer del flusso archiviato di tipo a [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Esempio

Vedere[strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) per un esempio d'uso di `rdbuf`.

## <a name="ostrstreamstr"></a><a name="str"></a>ostrstream::str

Chiama [freeze](../standard-library/strstreambuf-class.md#freeze) e quindi restituisce un puntatore all'inizio della sequenza controllata.

```cpp
char *str();
```

### <a name="return-value"></a>Valore restituito

Puntatore all'inizio della sequenza controllata.

### <a name="remarks"></a>Osservazioni

La funzione membro restituisce [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Esempio

Vedere [strstream::str](../standard-library/strstreambuf-class.md#str) per un `str`esempio che utilizza .

## <a name="see-also"></a>Vedere anche

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Sicurezza dei filettatura nella libreria standard di C](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmazione iostream](../standard-library/iostream-programming.md)\
[Convenzioni di iostream](../standard-library/iostreams-conventions.md)
