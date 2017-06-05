---
title: Classe basic_ofstream | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- basic_ofstream
- fstream/std::basic_ofstream
- fstream/std::basic_ofstream::close
- fstream/std::basic_ofstream::is_open
- fstream/std::basic_ofstream::open
- fstream/std::basic_ofstream::rdbuf
- fstream/std::basic_ofstream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_ofstream class
ms.assetid: 3bcc9c51-6dfc-4844-8fcc-22ef57c9dff1
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: f77cfe752aa297ea1237a7ac0467267d535ae852
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="basicofstream-class"></a>Classe basic_ofstream
Descrive un oggetto che controlla l'inserimento di elementi e oggetti codificati in un buffer di flusso della classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, con elementi di tipo `Elem`, i cui tratti di carattere sono determinati dalla classe `Tr`.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ofstream : public basic_ostream<Elem, Tr>
```  
  
#### <a name="parameters"></a>Parametri  
 `Elem`  
 L'elemento di base del buffer di file.  
  
 `Tr`  
 I tratti dell'elemento di base del buffer di file (in genere `char_traits`< `Elem`>).  
  
## <a name="remarks"></a>Note  
 Quando la specializzazione `wchar_t` di `basic_ofstream` scrive nel file, se il file è aperto in modalità testo scriverà una sequenza MBCS. La rappresentazione interna userà un buffer di caratteri `wchar_t`.  
  
 L'oggetto archivia un oggetto della classe `basic_filebuf`< `Elem`, `Tr`>.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come creare un oggetto `basic_ofstream` e scrivervi del testo.  
  
```  
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
  
|||  
|-|-|  
|[basic_ofstream](#basic_ofstream)|Crea un oggetto di tipo `basic_ofstream`.|  
  
### <a name="member-functions"></a>Funzioni membro  
  
|||  
|-|-|  
|[close](#close)|Chiude un file.|  
|[is_open](#is_open)|Determina se un file è aperto.|  
|[open](#open)|Apre un file.|  
|[rdbuf](#rdbuf)|Restituisce l'indirizzo del buffer del flusso archiviato.|  
|[swap](#swap)|Scambia il contenuto di questo `basic_ofstream` per il contenuto dell'oggetto `basic_ofstream` fornito.|  
  
### <a name="operators"></a>Operatori  
  
|||  
|-|-|  
|[operator=](#op_eq)|Assegna il contenuto di questo oggetto flusso. Si tratta di un'assegnazione di spostamento che implica un oggetto `rvalue reference` che non lascia alcuna copia.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<fstream>  
  
 **Spazio dei nomi:** std  
  
##  <a name="basic_ofstream"></a>  basic_ofstream::basic_ofstream  
 Crea un oggetto di tipo `basic_ofstream`.  
  
```
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
 `_Filename`  
 Nome del file da aprire.  
  
 `_Mode`  
 Una delle enumerazioni in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 La protezione di apertura file predefinita che equivale al parametro `shflag` in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
 `right`  
 Il riferimento rvalue all'oggetto `basic_ofstream` usato per inizializzare questo oggetto `basic_ofstream`.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore inizializza la classe base chiamando [basic_ostream](../standard-library/basic-ostream-class.md)( **sb**), dove **sb** è l'oggetto archiviato della classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. Inizializza anche **sb** chiamando `basic_filebuf`< `Elem`, `Tr`>.  
  
 Il secondo e il terzo costruttore inizializza la classe base chiamando `basic_ostream`( **sb**). Inizializza anche **sb** chiamando `basic_filebuf`< `Elem`, `Tr`> e quindi **sb**. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::out`). Se quest'ultima funzione restituisce un puntatore null, il costruttore chiama [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
 Il quarto costruttore è una funzione di copia. Inizializza l'oggetto con il contenuto di `right`, considerato come riferimento rvalue.  
  
### <a name="example"></a>Esempio  
  L'esempio seguente illustra come creare un oggetto `basic_ofstream` e scrivervi del testo.  
  
```  
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
  
##  <a name="close"></a>  basic_ofstream::close  
 Chiude un file.  
  
```
void close();
```  
  
### <a name="remarks"></a>Note  
 La funzione membro chiama [rdbuf](../standard-library/basic-ifstream-class.md#rdbuf)**->**[close](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Esempio  
  Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di **close**.  
  
##  <a name="is_open"></a>  basic_ofstream::is_open  
 Indica se un file è aperto.  
  
```
bool is_open() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 `true` se il file è aperto; in caso contrario, `false`.  
  
### <a name="remarks"></a>Note  
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
  
##  <a name="open"></a>  basic_ofstream::open  
 Apre un file.  
  
```
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
 `_Filename`  
 Nome del file da aprire.  
  
 `_Mode`  
 Una delle enumerazioni in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 La protezione di apertura file predefinita che equivale al parametro `shflag` in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Note  
 La funzione membro chiama [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; `ios_base::out`). Se tale funzione restituisce un puntatore null, la funzione chiama [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**).  
  
### <a name="example"></a>Esempio  
  Vedere [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) per un esempio di utilizzo di **open**.  
  
##  <a name="op_eq"></a>  basic_ofstream::operator=  
 Assegna il contenuto di questo oggetto flusso. Si tratta di un'assegnazione di spostamento che implica un oggetto `rvalue reference` che non lascia alcuna copia.  
  
```
basic_ofstream& operator=(basic_ofstream&& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Riferimento rvalue a un oggetto `basic_ofstream`.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce `*this`.  
  
### <a name="remarks"></a>Note  
 L'operatore del membro sostituisce i contenuti dell'oggetto usando i contenuti di `right`, gestiti come un riferimento rvalue.  
  
##  <a name="rdbuf"></a>  basic_ofstream::rdbuf  
 Restituisce l'indirizzo del buffer del flusso archiviato.  
  
```
basic_filebuf<Elem, Tr> *rdbuf() const
```  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce l'indirizzo del buffer del flusso archiviato.  
  
### <a name="example"></a>Esempio  
  Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di `rdbuf`.  
  
##  <a name="swap"></a>  basic_ofstream::swap  
 Scambia il contenuto di due oggetti `basic_ofstream`.  
  
```
void swap(basic_ofstream& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Riferimento `lvalue` a un altro oggetto `basic_ofstream`.  
  
### <a name="remarks"></a>Note  
 La funzione membro scambia il contenuto di questo oggetto con il contenuto di `right`.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe basic_ostream](../standard-library/basic-ostream-class.md)   
 [Thread safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programmazione di iostream](../standard-library/iostream-programming.md)   
 [Convenzioni di iostream](../standard-library/iostreams-conventions.md)



