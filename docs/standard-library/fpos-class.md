---
title: Classe fpos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- iosfwd/std::fpos
- fpos
- ios/std::fpos::seekpos
- ios/std::fpos::state
- ios/std::fpos::operator streamoff
dev_langs:
- C++
helpviewer_keywords:
- fpos class, about fpos class
- fpos class
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
caps.latest.revision: 20
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
ms.openlocfilehash: dfa9ee908b89c94b2eea95c450f67ca71031cf45
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="fpos-class"></a>Classe fpos
La classe modello descrive un oggetto che può archiviare tutte le informazioni necessarie per ripristinare un indicatore di posizione del file arbitrario all'interno di qualsiasi flusso. Un oggetto di classe fpos\< **St**> di fatto archivia almeno due oggetti membro:  
  
-   Un offset di byte, di tipo [streamoff](../standard-library/ios-typedefs.md#streamoff).  
  
-   Uno stato di conversione, per l'uso da parte di un oggetto della classe basic_filebuf, di tipo **St**, in genere `mbstate_t`.  
  
 Può anche archiviare una posizione di file arbitraria per l'uso da parte di un oggetto della classe [basic_filebuf](../standard-library/basic-filebuf-class.md), di tipo `fpos_t`. Per un ambiente con dimensioni del file limitate, tuttavia, a volte è possibile usare indifferentemente `streamoff` e `fpos_t`. Per un ambiente senza flussi con codifica dipendente dallo stato, è effettivamente possibile che `mbstate_t` non sia usato. Di conseguenza, il numero di oggetti membro archiviati può variare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
template <class Statetype>  
class fpos  
```  
  
#### <a name="parameters"></a>Parametri  
 *Statetype*  
 Informazioni di stato.  
  
### <a name="constructors"></a>Costruttori  
  
|||  
|-|-|  
|[fpos](#fpos)|Creare un oggetto che contiene informazioni su una posizione (offset) in un flusso.|  
  
### <a name="member-functions"></a>Funzioni membro  
  
|||  
|-|-|  
|[seekpos](#seekpos)|Usata internamente solo dalla libreria standard C++. Non chiamare questo metodo dal proprio codice.|  
|[state](#state)|Imposta o restituisce lo stato della conversione.|  
  
### <a name="operators"></a>Operatori  
  
|||  
|-|-|  
|[operator!=](#op_neq)|Testa gli indicatori di posizione del file per rilevare la disuguaglianza.|  
|[operator+](#op_add)|Incrementa un indicatore di posizione del file.|  
|[operator+=](#op_add_eq)|Incrementa un indicatore di posizione del file.|  
|[operator-](#operator-)|Decrementa un indicatore di posizione del file.|  
|[operator-=](#operator-_eq)|Decrementa un indicatore di posizione del file.|  
|[operator==](#op_eq_eq)|Testa gli indicatori di posizione del file per rilevare l'uguaglianza.|  
|[operator streamoff](#op_streamoff)|Esegue il cast del tipo `fpos` in oggetto di tipo `streamoff`.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<ios>  
  
 **Spazio dei nomi:** std  
  
##  <a name="fpos"></a>  fpos::fpos  
 Creare un oggetto che contiene informazioni su una posizione (offset) in un flusso.  
  
```  
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```  
  
### <a name="parameters"></a>Parametri  
 `_Off`  
 Offset nel flusso.  
  
 `_State`  
 Stato iniziale dell'oggetto `fpos`.  
  
 *_Filepos*  
 Offset nel flusso.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore archivia l'offset `_Off`, relativo all'inizio del file e nello stato di conversione iniziale (se importante). Se `_Off` è -1, l'oggetto risultante rappresenta una posizione nel flusso non valida.  
  
 Il secondo costruttore archivia un offset pari a zero e l'oggetto `_State`.  
  
##  <a name="op_neq"></a>  fpos::operator!=  
 Testa gli indicatori di posizione del file per rilevare la disuguaglianza.  
  
```  
bool operator!=(const fpos<Statetype>& right) const;
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Indicatore di posizione del file rispetto al quale eseguire il confronto.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se gli indicatori di posizione del file non sono uguali; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce `!(*this == right)`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// fpos_op_neq.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   fpos<int> pos1, pos2;  
   ifstream file;  
   char c;  
  
   // Compare two fpos object  
   if ( pos1 != pos2 )  
      cout << "File position pos1 and pos2 are not equal" << endl;  
   else  
      cout << "File position pos1 and pos2 are equal" << endl;  
  
   file.open( "fpos_op_neq.txt" );  
   file.seekg( 0 );   // Goes to a zero-based position in the file  
   pos1 = file.tellg( );  
   file.get( c);  
   cout << c << endl;  
  
   // Increment pos1  
   pos1 += 1;  
   file.get( c );  
   cout << c << endl;  
  
   pos1 = file.tellg( ) - fpos<int>( 2);  
   file.seekg( pos1 );  
   file.get( c );  
   cout << c << endl;  
  
   // Increment pos1  
   pos1 = pos1 + fpos<int>( 1 );  
   file.get(c);  
   cout << c << endl;  
  
   pos1 -= fpos<int>( 2 );  
   file.seekg( pos1 );  
   file.get( c );  
   cout << c << endl;  
  
   file.close( );  
}  
```  
  
##  <a name="op_add"></a>  fpos::operator+  
 Incrementa un indicatore di posizione del file.  
  
```  
fpos<Statetype> operator+(streamoff _Off) const;
```  
  
### <a name="parameters"></a>Parametri  
 `_Off`  
 Offset in base al quale si vuole incrementare l'indicatore di posizione del file.  
  
### <a name="return-value"></a>Valore restituito  
 Posizione nel file.  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce **fpos(\*this) +=** `_Off`.  
  
### <a name="example"></a>Esempio  
  Per un esempio di come usare `operator+`, vedere [operator!=](#op_neq).  
  
##  <a name="op_add_eq"></a>  fpos::operator+=  
 Incrementa un indicatore di posizione del file.  
  
```  
fpos<Statetype>& operator+=(streamoff _Off);
```  
  
### <a name="parameters"></a>Parametri  
 `_Off`  
 Offset in base al quale si vuole incrementare l'indicatore di posizione del file.  
  
### <a name="return-value"></a>Valore restituito  
 Posizione nel file.  
  
### <a name="remarks"></a>Note  
 La funzione membro aggiunge `_Off` all'oggetto membro offset archiviato e quindi restituisce **\*this**. Per il posizionamento all'interno di un file, il risultato in genere è valido solo per i flussi binari che non dispongono di una codifica dipendente dallo stato.  
  
### <a name="example"></a>Esempio  
  Per un esempio di come usare `operator+=`, vedere [operator!=](#op_neq).  
  
##  <a name="fpos__operator-"></a>  fpos::operator-  
 Decrementa un indicatore di posizione del file.  
  
```  
streamoff operator-(const fpos<Statetype>& right) const;
 
fpos<Statetype> operator-(streamoff _Off) const;
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Posizione del file.  
  
 `_Off`  
 Offset nel flusso.  
  
### <a name="return-value"></a>Valore restituito  
 La prima funzione membro restituisce `(streamoff)*this - (streamoff) right`. La seconda funzione membro restituisce `fpos(*this) -= _Off`.  
  
### <a name="example"></a>Esempio  
  Per un esempio di come usare `operator-`, vedere [operator!=](#op_neq).  
  
##  <a name="fpos__operator-_eq"></a>  fpos::operator-=  
 Decrementa un indicatore di posizione del file.  
  
```  
fpos<Statetype>& operator-=(streamoff _Off);
```  
  
### <a name="parameters"></a>Parametri  
 `_Off`  
 Offset nel flusso.  
  
### <a name="return-value"></a>Valore restituito  
 La funzione membro restituisce `fpos(*this) -= _Off`.  
  
### <a name="remarks"></a>Note  
 Per il posizionamento all'interno di un file, il risultato in genere è valido solo per i flussi binari che non dispongono di una codifica dipendente dallo stato.  
  
### <a name="example"></a>Esempio  
  Per un esempio di come usare `operator-=`, vedere [operator!=](#op_neq).  
  
##  <a name="op_eq_eq"></a>  fpos::operator==  
 Testa gli indicatori di posizione del file per rilevare l'uguaglianza.  
  
```  
bool operator==(const fpos<Statetype>& right) const;
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Indicatore di posizione del file rispetto al quale eseguire il confronto.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se gli indicatori di posizione del file sono uguali; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce `(streamoff)*this == (streamoff)right`.  
  
### <a name="example"></a>Esempio  
  Per un esempio di come usare `operator+=`, vedere [operator!=](#op_neq).  
  
##  <a name="op_streamoff"></a>  fpos::operator streamoff  
 Esegue il cast dell'oggetto di tipo `fpos` in oggetto di tipo `streamoff`.  
  
```  
operator streamoff() const;
```  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce l'oggetto membro offset archiviato e l'eventuale offset aggiuntivo archiviato come parte dell'oggetto membro `fpos_t`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// fpos_op_streampos.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   streamoff s;  
   ofstream file( "rdbuf.txt");  
  
   fpos<mbstate_t> f = file.tellp( );  
   // Is equivalent to ..  
   // streampos f = file.tellp( );  
   s = f;  
   cout << s << endl;  
}  
```  
  
```Output  
0  
```  
  
##  <a name="seekpos"></a>  fpos::seekpos  
 Questo metodo viene usato internamente solo dalla libreria standard C++. Non chiamare questo metodo dal proprio codice.  
  
```  
fpos_t seekpos() const;
```  
  
##  <a name="state"></a>  fpos::state  
 Imposta o restituisce lo stato della conversione.  
  
```  
Statetype state() const;

void state(Statetype _State);
```  
  
### <a name="parameters"></a>Parametri  
 `_State`  
 Nuovo stato di conversione.  
  
### <a name="return-value"></a>Valore restituito  
 Stato di conversione.  
  
### <a name="remarks"></a>Note  
 La prima funzione membro restituisce il valore archiviato nell'oggetto membro **St**. La seconda funzione membro archivia `_State` nell'oggetto membro **St**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// fpos_state.cpp  
// compile with: /EHsc  
#include <ios>  
#include <iostream>  
#include <fstream>  
  
int main() {  
   using namespace std;  
   streamoff s;  
   ifstream file( "fpos_state.txt" );  
  
   fpos<mbstate_t> f = file.tellg( );  
   char ch;  
   while ( !file.eof( ) )  
      file.get( ch );  
   s = f;  
   cout << f.state( ) << endl;  
   f.state( 9 );  
   cout << f.state( ) << endl;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Thread safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programmazione di iostream](../standard-library/iostream-programming.md)   
 [Convenzioni di iostream](../standard-library/iostreams-conventions.md)

