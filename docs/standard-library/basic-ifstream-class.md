---
title: Classe basic_ifstream | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- basic_ifstream
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_ifstream class
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
caps.latest.revision: 23
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
ms.openlocfilehash: e1027f916c8ab40a8e1040c3e1da47e5c15a3ae1
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="basicifstream-class"></a>Classe basic_ifstream
Descrive un oggetto che controlla l'estrazione di elementi e oggetti codificati da un buffer di flusso della classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> con elementi di tipo `Elem`, i cui tratti di carattere sono determinati dalla classe `Tr`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ifstream : public basic_istream<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametri  
 `Elem`  
 L'elemento di base del buffer di file.  
  
 `Tr`  
 I tratti dell'elemento di base del buffer di file (in genere `char_traits`< `Elem`>).  
  
## <a name="remarks"></a>Note  
 L'oggetto archivia un oggetto di classe `basic_filebuf`< `Elem`, `Tr`>.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra come leggere testo da un file.  
  
```  
// basic_ifstream_class.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_class.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
## <a name="input-basicifstreamclasstxt"></a>Input: basic_ifstream_class.txt  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
## <a name="output"></a>Output  
  
```  
This is the contents of basic_ifstream_class.txt.  
```  
  
### <a name="constructors"></a>Costruttori  
  
|||  
|-|-|  
|[basic_ifstream](#basic_ifstream)|Consente di inizializzare una nuova istanza di un oggetto `basic_ifstream`.|  
  
### <a name="member-functions"></a>Funzioni membro  
  
|||  
|-|-|  
|[close](#close)|Chiude un file.|  
|[is_open](#is_open)|Determina se un file è aperto.|  
|[open](#open)|Apre un file.|  
|[rdbuf](#rdbuf)|Restituisce l'indirizzo del buffer del flusso archiviato.|  
|[swap](#swap)|Scambia il contenuto di questo `basic_ifstream` con il contenuto del parametro `basic_ifstream` fornito.|  
  
### <a name="operators"></a>Operatori  
  
|||  
|-|-|  
|[operator=](#op_eq)|Assegna il contenuto di questo oggetto flusso. Si tratta di un'assegnazione di spostamento che implica un oggetto `rvalue` che non lascia alcuna copia.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<fstream>  
  
 **Spazio dei nomi:** std  
  
##  <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream  
 Costruisce un oggetto di tipo `basic_ifstream`.  
  
```  
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```  
  
### <a name="parameters"></a>Parametri  
 `_Filename`  
 Nome del file da aprire.  
  
 `_Mode`  
 Una delle enumerazioni in [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 La protezione di apertura file predefinita che equivale al parametro `shflag` in [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="remarks"></a>Note  
 Il primo costruttore inizializza la classe base chiamando [basic_istream](../standard-library/basic-istream-class.md)( `sb`), dove `sb` è l'oggetto archiviato di classe [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>. Inizializza anche `sb` chiamando `basic_filebuf`< `Elem`, `Tr`>.  
  
 Il secondo e il terzo costruttore inizializza la classe base chiamando `basic_istream`( `sb`). Inizializza anche `sb` chiamando [basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`>, quindi `sb`. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`). Se quest'ultima funzione restituisce un puntatore null, il costruttore chiama **setstate**( `failbit`).  
  
 Il quarto costruttore inizializza l'oggetto con il contenuto di `right`, considerato come riferimento rvalue.  
  
### <a name="example"></a>Esempio  
  L'esempio seguente illustra come leggere testo da un file. Per creare il file, vedere l'esempio per [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream).  
  
```  
// basic_ifstream_ctor.cpp  
// compile with: /EHsc  
  
#include <fstream>  
#include <iostream>  
  
using namespace std;  
  
int main(int argc, char **argv)  
{  
    ifstream ifs("basic_ifstream_ctor.txt");  
    if (!ifs.bad())  
    {  
        // Dump the contents of the file to cout.  
        cout << ifs.rdbuf();  
        ifs.close();  
    }  
}  
```  
  
##  <a name="close"></a>  basic_ifstream::close  
 Chiude un file.  
  
```  
void close();
```  
  
### <a name="remarks"></a>Note  
 La funzione membro chiama [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close).  
  
### <a name="example"></a>Esempio  
  Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di **close**.  
  
##  <a name="is_open"></a>  basic_ifstream::is_open  
 Determina se un file è aperto.  
  
```  
bool is_open() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 **true** se il file è aperto; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open).  
  
### <a name="example"></a>Esempio  
  Vedere [basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open) per un esempio di utilizzo di `is_open`.  
  
##  <a name="open"></a>  basic_ifstream::open  
 Apre un file.  
  
```  
void open(
    const char* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,  
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,  
    ios_base::openmode _Mode = ios_base::in,  
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
 La funzione membro chiama [rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; **ios_base::in**). Se l'apertura non viene eseguita, la funzione chiama [setstate](../standard-library/basic-ios-class.md#setstate)( **failbit**) che può generare un'eccezione ios_base::failure.  
  
### <a name="example"></a>Esempio  
  Vedere [basic_filebuf::open](../standard-library/basic-filebuf-class.md#open) per un esempio di utilizzo di **open**.  
  
##  <a name="op_eq"></a>  basic_ifstream::operator=  
 Assegna il contenuto di questo oggetto flusso. Si tratta di un'assegnazione di spostamento che implica un riferimento rvalue che non lascia alcuna copia.  
  
```  
basic_ifstream& operator=(basic_ifstream&& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Riferimento rvalue a un oggetto `basic_ifstream`.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce `*this`.  
  
### <a name="remarks"></a>Note  
 L'operatore del membro sostituisce i contenuti dell'oggetto usando i contenuti di `right`, gestiti come un riferimento rvalue. Per altre informazioni, vedere [Elementi lvalue e rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).  
  
##  <a name="rdbuf"></a>  basic_ifstream::rdbuf  
 Restituisce l'indirizzo del buffer del flusso archiviato.  
  
```  
basic_filebuf<Elem, Tr> *rdbuf() const 
```  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore a un oggetto [basic_filebuf](../standard-library/basic-filebuf-class.md) che rappresenta il buffer di flusso archiviato.  
  
### <a name="example"></a>Esempio  
  Vedere [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) per un esempio di utilizzo di `rdbuf`.  
  
##  <a name="swap"></a>  basic_ifstream::swap  
 Scambia il contenuto di due oggetti `basic_ifstream`.  
  
```  
void swap(basic_ifstream& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Riferimento a un altro buffer del flusso.  
  
### <a name="remarks"></a>Note  
 La funzione membro scambia il contenuto di questo oggetto con il contenuto di `right`.  
  
## <a name="see-also"></a>Vedere anche  
 [Thread safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programmazione di iostream](../standard-library/iostream-programming.md)   
 [Convenzioni di iostream](../standard-library/iostreams-conventions.md)


