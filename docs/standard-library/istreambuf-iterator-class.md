---
title: Classe istreambuf_iterator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istreambuf_iterator
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
dev_langs:
- C++
helpviewer_keywords:
- istreambuf_iterator class
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
caps.latest.revision: 19
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
ms.openlocfilehash: 942f61a053e77bf3d677f51cc30d39b5f4c76db6
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="istreambufiterator-class"></a>Classe istreambuf_iterator
La classe modello istreambuf_iterator descrive un oggetto iteratore di input che estrae gli elementi dei caratteri da un buffer del flusso di input, a cui accede tramite un oggetto archiviato di tipo puntatore a `basic_streambuf`\< **CharType**, **Traits**>.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class CharType class Traits = char_traits <CharType>>  
class istreambuf_iterator 
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```  
  
#### <a name="parameters"></a>Parametri  
 `CharType`  
 Tipo che rappresenta il tipo di carattere per istreambuf_iterator.  
  
 `Traits`  
 Tipo che rappresenta il tipo di carattere per istreambuf_iterator. Questo argomento è facoltativo e il valore predefinito è `char_traits`\< *CharType>.*  
  
## <a name="remarks"></a>Note  
 La classe istreambuf_iterator deve soddisfare i requisiti per un iteratore di input.  
  
 Dopo la costruzione o l'incremento di un oggetto della classe istreambuf_iterator con un puntatore archiviato diverso da Null, l'oggetto prova a estrarre e ad archiviare un oggetto di tipo **CharType** dal flusso di input associato. L'estrazione può essere tuttavia ritardata fino a quando l'oggetto non viene dereferenziato o copiato. Se l'estrazione ha esito negativo, l'oggetto sostituisce il puntatore archiviato con un puntatore Null, creando così un indicatore di fine della sequenza.  
  
### <a name="constructors"></a>Costruttori  
  
|||  
|-|-|  
|[istreambuf_iterator](#istreambuf_iterator)|Costruisce un `istreambuf_iterator` inizializzato per leggere i caratteri dal flusso di input.|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[char_type](#char_type)|Tipo che fornisce il tipo di carattere di `ostreambuf_iterator`.|  
|[int_type](#int_type)|Tipo che fornisce un tipo Integer per `istreambuf_iterator`.|  
|[istream_type](#istream_type)|Tipo che fornisce il tipo di flusso di `istream_iterator`.|  
|[streambuf_type](#streambuf_type)|Tipo che fornisce il tipo di flusso di `istreambuf_iterator`.|  
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Tipo che fornisce il tipo di tratti di `istream_iterator`.|  
  
### <a name="member-functions"></a>Funzioni membro  
  
|||  
|-|-|  
|[equal](#equal)|Test per verificare l'uguaglianza tra due iteratori del buffer del flusso di input.|  
  
### <a name="operators"></a>Operatori  
  
|||  
|-|-|  
|[operator*](#op_star)|L'operatore di dereferenziazione restituisce il carattere successivo del flusso.|  
|[operator++](#op_add_add)|Restituisce il carattere successivo del flusso di input oppure copia l'oggetto prima di incrementarlo e restituisce la copia.|  
|[operator->](#operator-_gt)|Restituisce il valore di un numero, se presente.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<iterator>  
  
 **Spazio dei nomi:** std  
  
##  <a name="char_type"></a>  istreambuf_iterator::char_type  
 Tipo che fornisce il tipo di carattere di `ostreambuf_iterator`.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo del parametro di modello **CharType**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// istreambuf_iterator_char_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   typedef istreambuf_iterator<char>::char_type CHT1;  
   typedef istreambuf_iterator<char>::traits_type CHTR1;  
  
   cout << "(Try the example: 'So many dots to be done'\n"  
        << " then an Enter key to insert into the output,\n"  
        << " & use a ctrl-Z Enter key combination to exit): ";  
  
   // istreambuf_iterator for input stream  
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );  
   ostreambuf_iterator<char> charOut ( cout );  
  
   // Used in conjunction with replace_copy algorithm  
   // to insert into output stream and replace spaces  
   // with dot-separators  
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),  
        charOut , ' ' , '.' );  
}  
```  
  
##  <a name="equal"></a>  istreambuf_iterator::equal  
 Test per verificare l'equivalenza tra due iteratori del buffer del flusso di input.  
  
```
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Iteratore per cui verificare l'equivalenza.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se entrambi gli oggetti `istreambuf_iterator` sono iteratori di fine flusso o se nessuno dei due è un iteratore di fine flusso; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Un intervallo viene definito da `istreambuf_iterator` in base alla posizione corrente e all'iteratore di fine flusso. Tuttavia, poiché tutti gli iteratori non di fine flusso sono equivalenti in base alla funzione membro **equal**, non è possibile definire intervalli secondari usando `istreambuf_iterator`. Gli operatori `==` e `!=` hanno la stessa semantica.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// istreambuf_iterator_equal.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "(Try the example: 'Hello world!'\n"  
        << " then an Enter key to insert into the output,\n"  
        << " & use a ctrl-Z Enter key combination to exit): ";  
  
   istreambuf_iterator<char> charReadIn1 ( cin );  
   istreambuf_iterator<char> charReadIn2 ( cin );  
  
   bool b1 = charReadIn1.equal ( charReadIn2 );  
  
   if (b1)  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
}  
```  
  
##  <a name="int_type"></a>  istreambuf_iterator::int_type  
 Tipo che fornisce un tipo Integer per `istreambuf_iterator`.  
  
```
typedef typename traits_type::int_type int_type;
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di **Traits::int_type**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// istreambuf_iterator_int_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   istreambuf_iterator<char>::int_type inttype1 = 100;  
   cout << "The inttype1 = " << inttype1 << "." << endl;  
}  
\* Output:   
The inttype1 = 100.  
*\  
```  
  
##  <a name="istream_type"></a>  istreambuf_iterator::istream_type  
 Tipo che fornisce il tipo di flusso di `istreambuf_iterator`.  
  
```
typedef basic_istream<CharType, Traits> istream_type;
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di `basic_istream`\< **CharType**, **Traits**>.  
  
### <a name="example"></a>Esempio  
  Vedere [istreambuf_iterator](#istreambuf_iterator) per un esempio di come dichiarare e usare `istream_type`.  
  
##  <a name="istreambuf_iterator"></a>  istreambuf_iterator::istreambuf_iterator  
 Costruisce un oggetto istreambuf_iterator inizializzato per la lettura di caratteri dal flusso di input.  
  
```
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```  
  
### <a name="parameters"></a>Parametri  
 `strbuf`  
 Buffer del flusso di input a cui viene collegato l'oggetto `istreambuf_iterator`.  
  
 `_Istr`  
 Flusso di input a cui viene collegato l'oggetto `istreambuf_iterator`.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore inizializza il puntatore del buffer del flusso di input con `strbuf`. Il secondo costruttore inizializza il puntatore del buffer del flusso di input con `_Istr`. `rdbuf` e quindi tenta di estrarre e archiviare un oggetto di tipo **CharType**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// istreambuf_iterator_istreambuf_iterator.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <algorithm>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Following declarations will not compile:  
   istreambuf_iterator<char>::istream_type &istrm = cin;  
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );  
  
   cout << "(Try the example: 'Oh what a world!'\n"  
      << " then an Enter key to insert into the output,\n"  
      << " & use a ctrl-Z Enter key combination to exit): ";  
   istreambuf_iterator<char> charReadIn ( cin );  
   ostreambuf_iterator<char> charOut ( cout );  
  
   // Used in conjunction with replace_copy algorithm  
   // to insert into output stream and replace spaces  
   // with hyphen-separators  
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),  
      charOut , ' ' , '-' );  
}  
```  
  
##  <a name="op_star"></a>  istreambuf_iterator::operator*  
 L'operatore di dereferenziazione restituisce il carattere successivo del flusso.  
  
```
CharType operator*() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Carattere successivo nel flusso.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// istreambuf_iterator_operator_deref.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "Type string of characters & enter to output it,\n"  
      << " with stream buffer iterators,(try: 'I'll be back.')\n"  
      << " repeat as many times as desired,\n"   
      << " then keystroke ctrl-Z Enter to exit program: ";  
   istreambuf_iterator<char> inpos ( cin );  
   istreambuf_iterator<char> endpos;  
   ostreambuf_iterator<char> outpos ( cout );  
   while ( inpos != endpos )  
   {  
 *outpos = *inpos;   //Put value of outpos equal to inpos  
      ++inpos;  
      ++outpos;  
   }  
}  
```  
  
##  <a name="op_add_add"></a>  istreambuf_iterator::operator++  
 Restituisce il carattere successivo del flusso di input oppure copia l'oggetto prima di incrementarlo e restituisce la copia.  
  
```
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto `istreambuf_iterator` o riferimento a un oggetto `istreambuf_iterator`.  
  
### <a name="remarks"></a>Note  
 Il primo operatore prova a estrarre e ad archiviare un oggetto di tipo **CharType** dal flusso di input associato. Il secondo operatore esegue una copia dell'oggetto, incrementa l'oggetto, quindi restituisce la copia.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// istreambuf_iterator_operator_incr.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   cout << "Type string of characters & enter to output it,\n"  
      << " with stream buffer iterators,(try: 'I'll be back.')\n"  
      << " repeat as many times as desired,\n"   
      << " then keystroke ctrl-Z Enter to exit program: ";  
   istreambuf_iterator<char> inpos ( cin );  
   istreambuf_iterator<char> endpos;  
   ostreambuf_iterator<char> outpos ( cout );  
   while ( inpos != endpos )  
   {  
 *outpos = *inpos;  
      ++inpos;   //Increment istreambuf_iterator  
      ++outpos;  
   }  
}  
```  
  
##  <a name="istreambuf_iterator__operator-_gt"></a>  istreambuf_iterator::operator-&gt;  
 Restituisce il valore di un numero, se presente.  
  
```
const Elem* operator->() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 L'operatore restituisce **&\*\*this**.  
  
##  <a name="streambuf_type"></a>  istreambuf_iterator::streambuf_type  
 Tipo che fornisce il tipo di flusso dell'oggetto istreambuf_iterator.  
  
```
typedef basic_streambuf<CharType, Traits> streambuf_type;
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di `basic_streambuf`\< **CharType**, **Traits**>.  
  
### <a name="example"></a>Esempio  
  Vedere [istreambuf_iterator](#istreambuf_iterator) per un esempio di come dichiarare e usare **istreambuf_type**.  
  
##  <a name="traits_type"></a>  istreambuf_iterator::traits_type  
 Tipo che fornisce il tipo di tratti di `istream_iterator`.  
  
```
typedef Traits traits_type;
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo del parametro di modello **Traits**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// istreambuf_iterator_traits_type.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
#include <algorithm>  
  
int main( )  
{  
   using namespace std;  
  
   typedef istreambuf_iterator<char>::char_type CHT1;  
   typedef istreambuf_iterator<char>::traits_type CHTR1;  
  
   cout << "(Try the example: 'So many dots to be done'\n"  
        << " then an Enter key to insert into the output,\n"  
        << " & use a ctrl-Z Enter key combination to exit): ";  
  
   // istreambuf_iterator for input stream  
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );  
   ostreambuf_iterator<char> charOut ( cout );  
  
   // Used in conjunction with replace_copy algorithm  
   // to insert into output stream and replace spaces  
   // with dot-separators  
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),  
        charOut , ' ' , '.' );  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Struct iterator](../standard-library/iterator-struct.md)   
 [\<iterator>](../standard-library/iterator.md)   
 [Thread safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Riferimento per la libreria standard C++](../standard-library/cpp-standard-library-reference.md)



