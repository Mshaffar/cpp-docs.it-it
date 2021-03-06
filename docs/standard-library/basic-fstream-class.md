---
title: Classe basic_fstream
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_fstream
- fstream/std::basic_fstream::close
- fstream/std::basic_fstream::is_open
- fstream/std::basic_fstream::open
- fstream/std::basic_fstream::rdbuf
- fstream/std::basic_fstream::swap
helpviewer_keywords:
- std::basic_fstream [C++]
- std::basic_fstream [C++], close
- std::basic_fstream [C++], is_open
- std::basic_fstream [C++], open
- std::basic_fstream [C++], rdbuf
- std::basic_fstream [C++], swap
ms.assetid: 8473817e-42a4-430b-82b8-b476c86bcf8a
ms.openlocfilehash: 80992430d6bef6fc46106452dfaa44cc0ed9e71c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376852"
---
# <a name="basic_fstream-class"></a>Classe basic_fstream

Viene descritto un oggetto che controlla l'inserimento e l'estrazione `Tr` di elementi e `Elem`oggetti codificati utilizzando un `Tr`buffer di flusso della classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`>, con elementi di tipo , i cui tratti di carattere sono determinati dalla classe .

## <a name="syntax"></a>Sintassi

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_fstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Parametri

*Elem*\
L'elemento di base del buffer di file.

*Tr*\
I tratti dell'elemento di base del buffer di file (in genere `char_traits`< `Elem`>).

## <a name="remarks"></a>Osservazioni

L'oggetto archivia un oggetto di classe `basic_filebuf`< `Elem`, `Tr`>.

> [!NOTE]
> Il puntatore get e il puntatore put di un oggetto fstream **NON** sono indipendenti l'uno dall'altro. Se il puntatore get si sposta, lo fa anche il puntatore put.

## <a name="example"></a>Esempio

L'esempio seguente mostra come creare un oggetto `basic_fstream` che consente la lettura e la scrittura.

```cpp
// basic_fstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    fstream fs("fstream.txt", ios::in | ios::out | ios::trunc);
    if (!fs.bad())
    {
        // Write to the file.
        fs << "Writing to a basic_fstream object..." << endl;
        fs.close();

        // Dump the contents of the file to cout.
        fs.open("fstream.txt", ios::in);
        cout << fs.rdbuf();
        fs.close();
    }
}
```

```Output
Writing to a basic_fstream object...
```

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[basic_fstream](#basic_fstream)|Costruisce un oggetto di tipo `basic_fstream`.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[Vicino](#close)|Chiude un file.|
|[is_open](#is_open)|Determina se un file è aperto.|
|[open](#open)|Apre un file.|
|[rdbuf](#rdbuf)|Restituisce l'indirizzo del buffer del flusso `Tr` archiviato, di tipo puntatore a [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`,>.|
|[Swap](#swap)|Scambia i contenuti di questo oggetto con quelli di un altro oggetto `basic_fstream`.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<fstream>

**Spazio dei nomi:** std

## <a name="basic_fstreambasic_fstream"></a><a name="basic_fstream"></a>basic_fstream::basic_fstream

Costruisce un oggetto di tipo `basic_fstream`.

```cpp
basic_fstream();

explicit basic_fstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_fstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_fstream(basic_fstream&& right);
```

### <a name="parameters"></a>Parametri

*_Filename*\
Nome del file da aprire.

*_Mode*\
Una delle enumerazioni in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
La protezione predefinita per l'apertura dei file, equivalente al parametro *shflag* in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Osservazioni

Il primo costruttore inizializza la classe`sb`base `sb` chiamando [basic_iostream](../standard-library/basic-iostream-class.md)( ), dove è l'oggetto archiviato della classe [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>. Viene inoltre `sb` inizializzato `basic_filebuf` \< chiamando **Elem**, **Tr**>.

Il secondo e il terzo costruttore inizializza la classe base chiamando `basic_iostream`( **sb**). Viene inoltre `sb` inizializzato `basic_filebuf` \< chiamando **Elem**, **Tr**> e quindi `_Mode` **sb.**[open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, ). Se quest'ultima funzione restituisce un puntatore`failbit`null, il costruttore chiama [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Il quarto costruttore inizializza l'oggetto con il contenuto di `right`, considerato come riferimento rvalue.

### <a name="example"></a>Esempio

Vedere [streampos](../standard-library/ios-typedefs.md#streampos) per un esempio di utilizzo di `basic_fstream`.

## <a name="basic_fstreamclose"></a><a name="close"></a>basic_fstream::chiudi

Chiude un file.

```cpp
void close();
```

### <a name="remarks"></a>Osservazioni

La funzione membro chiama [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Esempio

Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di `close`.

## <a name="basic_fstreamis_open"></a><a name="is_open"></a>basic_fstream::is_open

Determina se un file è aperto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valore restituito

**true** se il file è aperto; in caso contrario, **false**.

### <a name="remarks"></a>Osservazioni

La funzione membro restituisce [rdbuf](#rdbuf)**->**[is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Esempio

Vedere [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) per un esempio di utilizzo di `is_open`.

## <a name="basic_fstreamopen"></a><a name="open"></a>basic_fstream::aprire

Apre un file.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in | ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parametri

*_Filename*\
Nome del file da aprire.

*_Mode*\
Una delle enumerazioni in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
La protezione predefinita per l'apertura dei file, equivalente al parametro *shflag* in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Osservazioni

La funzione membro chiama [rdbuf](#rdbuf) **->** `_Mode` [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, ). Se tale funzione restituisce un puntatore `failbit`null, la funzione chiama [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Esempio

Per un esempio di utilizzo di `open` [basic_filebuf::open, vedere basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) .

## <a name="basic_fstreamoperator"></a><a name="op_eq"></a>basic_fstream::operatore

Assegna a questo oggetto il contenuto di un oggetto flusso specificato. Si tratta di un'assegnazione di spostamento che implica un rvalue che non lascia alcuna una copia.

```cpp
basic_fstream& operator=(basic_fstream&& right);
```

### <a name="parameters"></a>Parametri

*va bene*\
Riferimento lvalue a un oggetto `basic_fstream`.

### <a name="return-value"></a>Valore restituito

Restituisce `*this`.

### <a name="remarks"></a>Osservazioni

L'operatore membro sostituisce il contenuto dell'oggetto utilizzando il contenuto di *right*, considerato come un riferimento rvalue.

## <a name="basic_fstreamrdbuf"></a><a name="rdbuf"></a>basic_fstream::rdbuf

Restituisce l'indirizzo del buffer di flusso archiviato di tipo puntatore in [basic_filebuf](../standard-library/basic-filebuf-class.md)\< **Elem**, **Tr**>.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valore restituito

L'indirizzo del buffer di flusso archiviato.

### <a name="example"></a>Esempio

Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di `rdbuf`.

## <a name="basic_fstreamswap"></a><a name="swap"></a>basic_fstream::swap

Scambia il contenuto di due oggetti `basic_fstream`.

```cpp
void swap(basic_fstream& right);
```

### <a name="parameters"></a>Parametri

*va bene*\
Riferimento `lvalue` a un oggetto `basic_fstream`.

### <a name="remarks"></a>Osservazioni

La funzione membro scambia il contenuto di questo oggetto e il contenuto di *right*.

## <a name="see-also"></a>Vedere anche

[Sicurezza dei filettatura nella libreria standard di C](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmazione iostream](../standard-library/iostream-programming.md)\
[Convenzioni di iostream](../standard-library/iostreams-conventions.md)
