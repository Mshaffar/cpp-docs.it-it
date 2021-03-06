---
title: Classe basic_ofstream
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
helpviewer_keywords:
- std::basic_ofstream [C++]
- std::basic_ofstream [C++], close
- std::basic_ofstream [C++], is_open
- std::basic_ofstream [C++], open
- std::basic_ofstream [C++], rdbuf
- std::basic_ofstream [C++], swap
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
ms.openlocfilehash: f2d0facd92e0ef1935f8218a6d323a62edb81e5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376791"
---
# <a name="basic_ofstream-class"></a>Classe basic_ofstream

Descrive un oggetto che controlla l'inserimento di elementi e `Tr` oggetti codificati `Elem`in un buffer di flusso `Tr`della classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`>, con elementi di tipo , i cui tratti di carattere sono determinati dalla classe .

## <a name="syntax"></a>Sintassi

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ofstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Parametri

*Elem*\
L'elemento di base del buffer di file.

*Tr*\
I tratti dell'elemento di base del buffer di file (in genere `char_traits`< `Elem`>).

## <a name="remarks"></a>Osservazioni

Quando il **wchar_t** `basic_ofstream` la specializzazione delle scritture nel file, se il file viene aperto in modalità testo scriverà una sequenza MBCS. La rappresentazione interna userà un buffer di caratteri `wchar_t`.

L'oggetto archivia un oggetto di classe `basic_filebuf`< `Elem`, `Tr`>.

## <a name="example"></a>Esempio

L'esempio seguente illustra come creare un oggetto `basic_ofstream` e scrivervi del testo.

```cpp
// basic_ofstream_class.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[basic_ofstream](#basic_ofstream)|Crea un oggetto di tipo `basic_ofstream`.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[Vicino](#close)|Chiude un file.|
|[is_open](#is_open)|Determina se un file è aperto.|
|[open](#open)|Apre un file.|
|[rdbuf](#rdbuf)|Restituisce l'indirizzo del buffer del flusso archiviato.|
|[Swap](#swap)|Scambia il contenuto di questo `basic_ofstream` per il contenuto dell'oggetto `basic_ofstream` fornito.|

### <a name="operators"></a>Operatori

|Operatore|Descrizione|
|-|-|
|[operatore di comando](#op_eq)|Assegna il contenuto di questo oggetto flusso. Si tratta di un'assegnazione di spostamento che implica un oggetto `rvalue reference` che non lascia alcuna copia.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<fstream>

**Spazio dei nomi:** std

## <a name="basic_ofstreambasic_ofstream"></a><a name="basic_ofstream"></a>basic_ofstream::basic_ofstream

Crea un oggetto di tipo `basic_ofstream`.

```cpp
basic_ofstream();

explicit basic_ofstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ofstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

basic_ofstream(
    basic_ofstream&& right);
```

### <a name="parameters"></a>Parametri

*_Filename*\
Nome del file da aprire.

*_Mode*\
Una delle enumerazioni in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*\
La protezione di apertura file predefinita che equivale al parametro `shflag` in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

*va bene*\
Il riferimento rvalue all'oggetto `basic_ofstream` usato per inizializzare questo oggetto `basic_ofstream`.

### <a name="remarks"></a>Osservazioni

Il primo costruttore inizializza la [basic_ostream](../standard-library/basic-ostream-class.md)classe`sb`base `sb` chiamando basic_ostream ( ), `Tr` dove è l'oggetto archiviato della classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`>. Inizializza anche `sb` chiamando `basic_filebuf`< `Elem`, `Tr`>.

Il secondo e il terzo costruttore inizializza la classe base chiamando `basic_ostream`( **sb**). Viene inoltre `sb` inizializzato `basic_filebuf` <  `Elem` `Tr` chiamando , `sb`> e quindi . [aperto](../standard-library/basic-filebuf-class.md#open) `_Filename`( `_Mode` `ios_base::out`, &#124; ). Se quest'ultima funzione restituisce un puntatore`failbit`null, il costruttore chiama [setstate](../standard-library/basic-ios-class.md#setstate)( ).

Il quarto costruttore è una funzione di copia. Inizializza l'oggetto con il contenuto di *right*, considerato come un riferimento rvalue.

### <a name="example"></a>Esempio

L'esempio seguente illustra come creare un oggetto `basic_ofstream` e scrivervi del testo.

```cpp
// basic_ofstream_ctor.cpp
// compile with: /EHsc
#include <fstream>

using namespace std;

int main(int argc, char **argv)
{
    ofstream ofs("C:\\ofstream.txt");
    if (!ofs.bad())
    {
        ofs << "Writing to a basic_ofstream object..." << endl;
        ofs.close();
    }
}
```

## <a name="basic_ofstreamclose"></a><a name="close"></a>basic_ofstream::chiudere

Chiude un file.

```cpp
void close();
```

### <a name="remarks"></a>Osservazioni

La funzione membro chiama [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[close](../standard-library/basic-filebuf-class.md#close).

### <a name="example"></a>Esempio

Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di `close`.

## <a name="basic_ofstreamis_open"></a><a name="is_open"></a>basic_ofstream::is_open

Indica se un file è aperto.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Valore restituito

**true** se il file è aperto; in caso contrario, **false**.

### <a name="remarks"></a>Osservazioni

La funzione membro restituisce [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).

### <a name="example"></a>Esempio

```cpp
// basic_ofstream_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   // Open and close with a basic_filebuf
   file.rdbuf( )->open( "basic_ofstream_is_open.txt", ios::in );
   file.close( );
   if (file.is_open())
      cout << "it's open" << endl;
   else
      cout << "it's closed" << endl;
}
```

## <a name="basic_ofstreamopen"></a><a name="open"></a>basic_ofstream::aprire

Apre un file.

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::out,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::out,
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
La protezione di apertura file predefinita che equivale al parametro `shflag` in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="remarks"></a>Osservazioni

La funzione membro chiama [rdbuf](#rdbuf) **->** `_Mode` [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, &#124; `ios_base::out`). Se tale funzione restituisce un puntatore`failbit`null, la funzione chiama [setstate](../standard-library/basic-ios-class.md#setstate)( ).

### <a name="example"></a>Esempio

Vedere [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) per un `open`esempio che utilizza .

## <a name="basic_ofstreamoperator"></a><a name="op_eq"></a>basic_ofstream::operatore

Assegna il contenuto di questo oggetto flusso. Si tratta di un'assegnazione di spostamento che implica un oggetto `rvalue reference` che non lascia alcuna copia.

```cpp
basic_ofstream& operator=(basic_ofstream&& right);
```

### <a name="parameters"></a>Parametri

*va bene*\
Riferimento rvalue a un oggetto `basic_ofstream`.

### <a name="return-value"></a>Valore restituito

Restituisce `*this`.

### <a name="remarks"></a>Osservazioni

L'operatore membro sostituisce il contenuto dell'oggetto utilizzando il contenuto di *right*, considerato come un riferimento rvalue.

## <a name="basic_ofstreamrdbuf"></a><a name="rdbuf"></a>basic_ofstream::rdbuf

Restituisce l'indirizzo del buffer del flusso archiviato.

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>Valore restituito

Restituisce l'indirizzo del buffer del flusso archiviato.

### <a name="example"></a>Esempio

Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di `rdbuf`.

## <a name="basic_ofstreamswap"></a><a name="swap"></a>basic_ofstream::swap

Scambia il contenuto di due oggetti `basic_ofstream`.

```cpp
void swap(basic_ofstream& right);
```

### <a name="parameters"></a>Parametri

*va bene*\
Riferimento `lvalue` a un altro oggetto `basic_ofstream`.

### <a name="remarks"></a>Osservazioni

La funzione membro scambia il contenuto di questo oggetto per il contenuto di *right*.

## <a name="see-also"></a>Vedere anche

[Classe basic_ostream](../standard-library/basic-ostream-class.md)\
[Sicurezza dei filettatura nella libreria standard di C](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmazione iostream](../standard-library/iostream-programming.md)\
[Convenzioni di iostream](../standard-library/iostreams-conventions.md)
