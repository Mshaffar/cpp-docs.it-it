---
title: Operatori &lt;iterator&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: b7c664f0-49d4-4993-b5d1-9ac4859fdddc
caps.latest.revision: 10
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: a369890d41b58fb3865780291822b4e7e045e919
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="ltiteratorgt-operators"></a>Operatori &lt;iterator&gt;
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator+](#op_add)|  
|[operator-](#operator-)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 Verifica se l'oggetto iteratore a sinistra dell'operatore non è uguale all'oggetto iteratore a destra.  
  
```  
template <class RandomIterator>  
bool operator!=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator!=(const istream_iterator<Type, CharType, Traits, Distance>& left, const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator!=(const istreambuf_iterator<CharType, Traits>& left, const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **iteratore**.  
  
 `right`  
 Oggetto di tipo **iteratore**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se gli oggetti iteratore sono uguali; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Un oggetto iteratore è uguale a un altro se entrambi puntano agli stessi elementi in un contenitore. Se due iteratori puntano a elementi diversi in un contenitore, non sono uguali.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_ne.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 9 ; ++i )    
   {  
      vec.push_back ( i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++ )  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 != rVPOS2 )  
      cout << "The iterators are not equal." << endl;  
   else  
      cout << "The iterators are equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 1 2 3 4 5 6 7 8 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 8.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 7.  
The iterators are not equal.  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
 Verifica se l'oggetto iteratore a sinistra dell'operatore è uguale all'oggetto iteratore a destra.  
  
```  
template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
bool operator==(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);

template <class Type, class CharType, class Traits, class Distance>  
bool operator==(
    const istream_iterator<Type, CharType, Traits, Distance>& left,  
    const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>  
bool operator==(
    const istreambuf_iterator<CharType, Traits>& left,  
    const istreambuf_iterator<CharType, Traits>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo iteratore.  
  
 `right`  
 Oggetto di tipo iteratore.  
  
### <a name="return-value"></a>Valore restituito  
 `true` se gli oggetti iteratore sono uguali; in caso contrario, `false`.  
  
### <a name="remarks"></a>Note  
 Un oggetto iteratore è uguale a un altro se entrambi puntano agli stessi elementi in un contenitore. Se due iteratori puntano a elementi diversi in un contenitore, non sono uguali.  
  
 I primi due operatori modello restituiscono true solo se `left` e `right` archiviano lo stesso iteratore. Il terzo operatore modello restituisce true solo se `left` e `right` archiviano lo stesso puntatore del flusso. Il quarto operatore modello restituisce ` left.equal ( right)`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_eq.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 1 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the first "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
        << "element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 == rVPOS2 )  
      cout << "The iterators are equal." << endl;  
   else  
      cout << "The iterators are not equal." << endl;  
}  
```  
  
```Output  
The vector vec is: ( 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterators are equal.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterators are not equal.  
```  
  
##  <a name="op_lt"></a>  operator&lt;  
 Verifica se l'oggetto iteratore a sinistra dell'operatore è minore all'oggetto iteratore a destra.  
  
```  
template <class RandomIterator>  
bool operator<(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **iteratore**.  
  
 `right`  
 Oggetto di tipo **iteratore**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'iteratore a sinistra dell'espressione è minore dell'iteratore a destra; **false** se è maggiore o uguale all'iteratore a destra.  
  
### <a name="remarks"></a>Note  
 Un oggetto iteratore è minore di un altro se punta a un elemento che si trova in una posizione precedente nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore. Un oggetto iteratore non è minore di un altro se punta allo stesso elemento dell'altro o a un elemento che si trova in una posizione successiva nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_lt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for ( i = 0 ; i < 6 ; ++i )  
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   // Initializing reverse_iterators to the last element  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1& rVPOS2 initially point to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 < rVPOS2 )  
      cout << "The iterator rVPOS1 is less than"  
              << " the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is not less than"  
              << " the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1& rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is not less than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
```  
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
 Verifica se l'oggetto iteratore a sinistra dell'operatore è minore o uguale all'oggetto iteratore a destra.  
  
```  
template <class RandomIterator>  
bool operator<=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo iteratore.  
  
 `right`  
 Oggetto di tipo iteratore.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'iteratore a sinistra dell'espressione è minore o uguale all'iteratore a destra; **false** se è maggiore dell'iteratore a destra.  
  
### <a name="remarks"></a>Note  
 Un oggetto iteratore è minore o uguale a un altro se punta allo stesso elemento o a un elemento che si trova in una posizione precedente nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore. Un oggetto iteratore è maggiore di un altro se punta a un elemento che si trova in una posizione successiva nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_le.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ) + 1,   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS2++;  
   cout << "The iterator rVPOS2 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 <= rVPOS2 )  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS2 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
The iterator rVPOS2 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_gt"></a>  operator&gt;  
 Verifica se l'oggetto iteratore a sinistra dell'operatore è maggiore dell'oggetto iteratore a destra.  
  
```  
template <class RandomIterator>  
bool operator>(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo iteratore.  
  
 `right`  
 Oggetto di tipo iteratore.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'iteratore a sinistra dell'espressione è maggiore dell'iteratore a destra; **false** se è minore o uguale all'iteratore a destra.  
  
### <a name="remarks"></a>Note  
 Un oggetto iteratore è maggiore di un altro se punta a un elemento che si trova in una posizione successiva nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore. Un oggetto iteratore non è maggiore di un altro se punta allo stesso elemento dell'altro o a un elemento che si trova in una posizione precedente nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_gt.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 > rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than "  
              << "the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than or "  
              << "equal to the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than the iterator rVPOS2.  
```  
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
 Verifica se l'oggetto iteratore a sinistra dell'operatore è maggiore o uguale all'oggetto iteratore a destra.  
  
```  
template <class RandomIterator>  
bool operator>=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo iteratore.  
  
 `right`  
 Oggetto di tipo iteratore.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'iteratore a sinistra dell'espressione è maggiore o uguale all'iteratore a destra; **false** se è minore dell'iteratore a destra.  
  
### <a name="remarks"></a>Note  
 Un oggetto iteratore è maggiore o uguale a un altro se punta allo stesso elemento o a un elemento che si trova in una posizione successiva nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore. Un oggetto iteratore è minore di un altro se punta a un elemento che si trova in una posizione precedente nel contenitore rispetto all'elemento a cui punta l'altro oggetto iteratore.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_ge.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
           rVPOS2 = vec.rbegin ( ) + 1;  
  
   cout << "The iterator rVPOS1 initially points to the "  
           << "first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   cout << "The iterator rVPOS2 initially points to the "  
           << "second element\n in the reversed sequence: "  
           << *rVPOS2 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
  
   rVPOS1++;  
   cout << "The iterator rVPOS1 now points to the second "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   if ( rVPOS1 >= rVPOS2 )  
      cout << "The iterator rVPOS1 is greater than or "  
              << "equal to the iterator rVPOS2." << endl;  
   else  
      cout << "The iterator rVPOS1 is less than "  
              << "the iterator rVPOS2." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 initially points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is less than the iterator rVPOS2.  
The iterator rVPOS1 now points to the second element  
 in the reversed sequence: 8.  
The iterator rVPOS1 is greater than or equal to the iterator rVPOS2.  
```  
  
##  <a name="op_add"></a>  operator+  
 Aggiunge un offset a un iteratore e restituisce un oggetto `move_iterator` o un oggetto `reverse_iterator` che punta all'elemento inserito in corrispondenza della nuova posizione dell'offset.  
  
```  
template <class RandomIterator, class Diff>  
move_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const move_iterator<RandomIterator>& right);

template <class RandomIterator>  
reverse_iterator<RandomIterator>  
operator+(
    Diff _Off,  
    const reverse_iterator<RandomIterator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `_Off`  
 Numero di posizioni in base alle quali deve essere eseguito l'offset di move_iterator const o reverse_iterator const.  
  
 `right`  
 Iteratore di cui deve essere eseguito l'offset.  
  
### <a name="return-value"></a>Valore restituito  
 Somma `right` + `_Off`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_insert.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )  {  
      vec.push_back ( 2 * i );  
      }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );  
  
   cout << "The iterator rVPOS1 initially points to "  
           << "the first element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
  
   vector<int>::difference_type diff = 4;  
   rVPOS1 = diff +rVPOS1;  
  
   cout << "The iterator rVPOS1 now points to the fifth "  
           << "element\n in the reversed sequence: "  
           << *rVPOS1 << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterator rVPOS1 initially points to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS1 now points to the fifth element  
 in the reversed sequence: 2.  
```  
  
##  <a name="operator-"></a>  operator-  
 Sottrae un iteratore da un altro e restituisce la differenza.  
  
```  
template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const move_iterator<RandomIterator1>& left,  
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>  
Tdiff operator-(
    const reverse_iterator<RandomIterator1>& left,  
    const reverse_iterator<RandomIterator2>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Iteratore.  
  
 `right`  
 Iteratore.  
  
### <a name="return-value"></a>Valore restituito  
 Differenza tra due iteratori `.`.  
  
### <a name="remarks"></a>Note  
 Il primo operatore modello restituisce `left.base() - right.base()`.  
  
 Il secondo operatore modello restituisce `right.current - left.current`.  
  
 `Tdiff` è determinato dal tipo dell'espressione restituita. Altrimenti, è `RandomIterator1::difference_type`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// iterator_op_sub.cpp  
// compile with: /EHsc  
#include <iterator>  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   vector<int> vec;  
   for (i = 0 ; i < 6 ; ++i )    
   {  
      vec.push_back ( 2 * i );  
   }  
  
   vector <int>::iterator vIter;  
  
   cout << "The initial vector vec is: ( ";  
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)  
      cout << *vIter << " ";  
   cout << ")." << endl;  
  
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),   
          rVPOS2 = vec.rbegin ( );  
  
   cout << "The iterators rVPOS1 & rVPOS2 initially point to "  
        << "the first element\n in the reversed sequence: "  
        << *rVPOS1 << "." << endl;  
  
   for (i = 1; i < 5; ++i)    
   {  
      rVPOS2++;  
   }  
   cout << "The iterator rVPOS2 now points to the fifth "  
        << "element\n in the reversed sequence: "  
        << *rVPOS2 << "." << endl;  
  
   vector<int>::difference_type diff = rVPOS2 - rVPOS1;  
   cout << "The difference: rVPOS2 - rVPOS1= "  
        << diff << "." << endl;  
}  
```  
  
```Output  
The initial vector vec is: ( 0 2 4 6 8 10 ).  
The iterators rVPOS1 & rVPOS2 initially point to the first element  
 in the reversed sequence: 10.  
The iterator rVPOS2 now points to the fifth element  
 in the reversed sequence: 2.  
The difference: rVPOS2 - rVPOS1= 4.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<iterator>](../standard-library/iterator.md)

