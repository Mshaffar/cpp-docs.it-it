---
title: Operatori &lt;list&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
caps.latest.revision: 7
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 5713a02d534f8e4e2245ba3d181d78c529adbe79
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="ltlistgt-operators"></a>Operatori &lt;list&gt;
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 Verifica se l'oggetto elenco a sinistra dell'operatore non è uguale all'oggetto elenco a destra.  
  
```
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **list**.  
  
 `right`  
 Oggetto di tipo **list**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se gli elenchi non sono uguali; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Il confronto tra gli oggetti elenco si basa su un confronto a coppie dei relativi elementi. Due elenchi sono uguali se hanno lo stesso numero di elementi e se i rispettivi elementi hanno gli stessi valori. In caso contrario, non sono uguali.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// list_op_ne.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
list <int> c1, c2;  
c1.push_back( 1 );  
c2.push_back( 2 );  
  
if ( c1 != c2 )  
cout << "Lists not equal." << endl;  
else  
cout << "Lists equal." << endl;  
}  
\* Output:  
Lists not equal.  
*\  
```  
  
##  <a name="op_lt"></a>  operator&lt;  
 Verifica se l'oggetto elenco a sinistra dell'operatore è minore dell'oggetto elenco a destra.  
  
```
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **list**.  
  
 `right`  
 Oggetto di tipo **list**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'elenco a sinistra dell'operatore è minore ma non uguale all'elenco a destra; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Il confronto tra gli oggetti elenco si basa su un confronto a coppie dei relativi elementi. La relazione minore di tra due oggetti si basa su un confronto della prima coppia di elementi non uguali.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// list_op_lt.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 < c2 )  
      cout << "List c1 is less than list c2." << endl;  
   else  
      cout << "List c1 is not less than list c2." << endl;  
}  
\* Output:   
List c1 is less than list c2.  
*\   
```  
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
 Verifica se l'oggetto elenco a sinistra dell'operatore è minore o uguale all'oggetto elenco a destra.  
  
```
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **list**.  
  
 `right`  
 Oggetto di tipo **list**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'elenco a sinistra dell'operatore è minore o uguale all'elenco a destra; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Il confronto tra gli oggetti elenco si basa su un confronto a coppie dei relativi elementi. La relazione minore di o uguale a tra due oggetti si basa su un confronto della prima coppia di elementi non uguali.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// list_op_le.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 <= c2 )  
      cout << "List c1 is less than or equal to list c2." << endl;  
   else  
      cout << "List c1 is greater than list c2." << endl;  
}  
\* Output:   
List c1 is less than or equal to list c2.  
*\  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
 Verifica se l'oggetto elenco a sinistra dell'operatore è uguale all'oggetto elenco a destra.  
  
```
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **list**.  
  
 `right`  
 Oggetto di tipo **list**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'elenco a sinistra dell'operatore è uguale all'elenco a destra; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Il confronto tra gli oggetti elenco si basa su un confronto a coppie dei relativi elementi. Due elenchi sono uguali se hanno lo stesso numero di elementi e se i rispettivi elementi hanno gli stessi valori. In caso contrario, non sono uguali.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// list_op_eq.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
int main( )   
{  
   using namespace std;   
  
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c2.push_back( 1 );  
  
   if ( c1 == c2 )  
      cout << "The lists are equal." << endl;  
   else  
      cout << "The lists are not equal." << endl;  
}  
\* Output:   
The lists are equal.  
*\  
```  
  
##  <a name="op_gt"></a>  operator&gt;  
 Verifica se l'oggetto elenco a sinistra dell'operatore è maggiore dell'oggetto elenco a destra.  
  
```
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **list**.  
  
 `right`  
 Oggetto di tipo **list**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'elenco a sinistra dell'operatore è maggiore dell'elenco a destra; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Il confronto tra gli oggetti elenco si basa su un confronto a coppie dei relativi elementi. La relazione maggiore di tra due oggetti si basa su un confronto della prima coppia di elementi non uguali.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// list_op_gt.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 > c2 )  
      cout << "List c1 is greater than list c2." << endl;  
   else  
      cout << "List c1 is not greater than list c2." << endl;  
}  
\* Output:   
List c1 is greater than list c2.  
*\  
```  
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
 Verifica se l'oggetto elenco a sinistra dell'operatore è maggiore o uguale all'oggetto elenco a destra.  
  
```
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `left`  
 Oggetto di tipo **list**.  
  
 `right`  
 Oggetto di tipo **list**.  
  
### <a name="return-value"></a>Valore restituito  
 **true** se l'elenco a sinistra dell'operatore è maggiore o uguale all'elenco a destra; in caso contrario, **false**.  
  
### <a name="remarks"></a>Note  
 Il confronto tra gli oggetti elenco si basa su un confronto a coppie dei relativi elementi. La relazione maggiore di o uguale a tra due oggetti si basa su un confronto della prima coppia di elementi non uguali.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// list_op_ge.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 >= c2 )  
      cout << "List c1 is greater than or equal to list c2." << endl;  
   else  
      cout << "List c1 is less than list c2." << endl;  
}  
\* Output:   
List c1 is greater than or equal to list c2.  
*\  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<list>](../standard-library/list.md)



