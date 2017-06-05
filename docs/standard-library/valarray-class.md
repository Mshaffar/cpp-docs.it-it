---
title: Classe valarray | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- valarray
- valarray/std::valarray
- valarray/std::valarray::value_type
- valarray/std::valarray::apply
- valarray/std::valarray::cshift
- valarray/std::valarray::free
- valarray/std::valarray::max
- valarray/std::valarray::min
- valarray/std::valarray::resize
- valarray/std::valarray::shift
- valarray/std::valarray::size
- valarray/std::valarray::sum
- valarray/std::valarray::swap
dev_langs:
- C++
helpviewer_keywords:
- valarray class
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
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
ms.openlocfilehash: b54bd0f6ca1dcd2efba32817c9c732045775cd8c
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="valarray-class"></a>Classe valarray
La classe modello descrive un oggetto che controlla una sequenza di elementi di tipo **Type** archiviati come matrice, progettati per l'esecuzione di operazioni matematiche ad alta velocità e ottimizzati per le prestazioni di calcolo.  
  
## <a name="remarks"></a>Note  
 La classe è una rappresentazione del concetto matematico di insieme ordinato di valori e gli elementi sono numerati in sequenza a partire da zero. La classe viene descritta come simile a un contenitore perché supporta parte delle funzionalità supportate da contenitori sequenziali di prima classe, come [vector](../standard-library/vector-class.md). Differisce dalla classe modello vector per due aspetti importanti:  
  
-   Definisce numerose operazioni aritmetiche tra elementi corrispondenti di oggetti **valarray\<Type>** dello stesso tipo e della stessa lunghezza, come *xarr* = cos( *yarr*) + sin( *zarr*).  
  
-   Definisce diversi modi interessanti per impostare come indice inferiore un oggetto **valarray\<Type>** tramite l'overload di [operator&#91;&#93;](#op_at).  
  
 Un oggetto di classe **Type**:  
  
-   Ha un costruttore predefinito pubblico, un distruttore, un costruttore di copia e un operatore di assegnazione, con un comportamento convenzionale.  
  
-   Definisce le funzioni matematiche e gli operatori aritmetici, come necessario, definiti per i tipi a virgola mobile, con un comportamento convenzionale.  
  
 In particolare, non possono esistere sottili differenze tra il costruttore di copia e la costruzione predefinita seguita dall'assegnazione. Nessuna delle operazioni sugli oggetti di classe **Type** può generare eccezioni.  
  
### <a name="constructors"></a>Costruttori  
  
|||  
|-|-|  
|[valarray](#valarray)|Costruisce un oggetto `valarray` di una dimensione specifica o con elementi di un determinato valore oppure come copia di un altro oggetto `valarray` o subset di un altro oggetto `valarray`.|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[value_type](#value_type)|Tipo che rappresenta il tipo di elemento archiviato in un oggetto `valarray`.|  
  
### <a name="member-functions"></a>Funzioni membro  
  
|||  
|-|-|  
|[apply](#apply)|Applica una funzione specificata a ogni elemento di un oggetto `valarray`.|  
|[cshift](#cshift)|Sposta ciclicamente tutti gli elementi in un oggetto `valarray` in base a un numero specificato di posizioni.|  
|[free](#free)|Libera la memoria usata da `valarray`.|  
|[max](#max)|Trova l'elemento più grande in un oggetto `valarray`.|  
|[min](#min)|Trova l'elemento più piccolo in un oggetto `valarray`.|  
|[resize](#resize)|Modifica il numero di elementi in un oggetto `valarray` in base a un numero specificato, aggiungendo o rimuovendo elementi nel modo necessario.|  
|[shift](#shift)|Sposta tutti gli elementi in un oggetto `valarray` in base a un numero specificato di posizioni.|  
|[size](#size)|Trova il numero di elementi in un oggetto `valarray`.|  
|[sum](#sum)|Determina la somma di tutti gli elementi in un oggetto `valarray` di lunghezza diversa da zero.|  
|[swap](#swap)||  
  
### <a name="operators"></a>Operatori  
  
|||  
|-|-|  
|[operator!](#op_not)|Operatore unario che ottiene i valori `NOT` logici di ogni elemento in un oggetto `valarray`.|  
|[operator%=](#op_mod_eq)|Ottiene il resto della divisione degli elementi di una matrice elemento per elemento per un oggetto `valarray` specificato o per un valore del tipo di elemento.|  
|[operator&=](#op_amp_eq)|Ottiene l'operatore `AND` bit per bit di elementi in una matrice con gli elementi corrispondenti in un oggetto `valarray` specificato o con un valore del tipo di elemento.|  
|[operator>>=](#op_gt_gt_eq)|Sposta verso destra i bit per ogni elemento di un operando `valarray` di un numero specificato di posizioni o in base a una quantità di elementi specificata da un secondo oggetto `valarray`.|  
|[operator<<=](#op_lt_lt_eq)|Sposta verso sinistra i bit per ogni elemento di un operando `valarray` di un numero specificato di posizioni o in base a una quantità di elementi specificata da un secondo oggetto `valarray`.|  
|[operator*=](#op_star_eq)|Moltiplica gli elementi di un oggetto `valarray` specificato o di un valore del tipo di elemento, elemento per elemento, per un operando `valarray`.|  
|[operator+](#op_add)|Operatore unario che applica un segno più a ogni elemento in un oggetto `valarray`.|  
|[operator+=](#op_add_eq)|Aggiunge gli elementi di un oggetto `valarray` specificato o di un valore del tipo di elemento, elemento per elemento, a un operando `valarray`.|  
|[operator-](#operator-)|Operatore unario che applica un segno meno a ogni elemento in un oggetto `valarray`.|  
|[operator-=](#operator-_eq)|Sottrae gli elementi di un oggetto `valarray` specificato o di un valore del tipo di elemento, elemento per elemento, da un operando `valarray`.|  
|[operator/=](#op_div_eq)|Divide un operando `valarray` elemento per elemento per gli elementi di un oggetto `valarray` specificato o di un valore del tipo di elemento.|  
|[operator=](#op_eq)|Assegna elementi a un oggetto `valarray` i cui valori sono specificati direttamente o come parti di un altro oggetto `valarray` oppure da `slice_array`, `gslice_array`, `mask_array` o `indirect_array`.|  
|[operator&#91;&#93;](#op_at)|Restituisce un riferimento a un elemento o al relativo valore in corrispondenza di un indice o un subset specificato.|  
|[operator^=](#op_xor_eq)|Ottiene l'operatore OR logico esclusivo elemento per elemento (`XOR`) di una matrice con un oggetto valarray specificato o un valore del tipo di elemento.|  
|[operator&#124;=](#op_or_eq)|Ottiene l'operatore `OR` bit per bit di elementi in una matrice con gli elementi corrispondenti in un oggetto `valarray` specificato o con un valore del tipo di elemento.|  
|[operator~](#op_dtor)|Operatore unario che ottiene i valori `NOT` bit per bit di ogni elemento in un oggetto `valarray`.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<valarray>  
  
 **Spazio dei nomi:** std  
  
##  <a name="apply"></a>  valarray::apply  
 Applica una funzione specificata a ogni elemento di un oggetto valarray.  
  
```  
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```  
  
### <a name="parameters"></a>Parametri  
 *_Func(Type)*  
 Oggetto funzione da applicare a ogni elemento dell'operando valarray.  
  
 *_Func(const Type&)*  
 Oggetto funzione per const da applicare a ogni elemento dell'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray con l'applicazione di `_Func` agli elementi dell'operando valarray elemento per elemento.  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce un oggetto di classe [valarray](../standard-library/valarray-class.md)**\<Type>**, di lunghezza [size](#size), di cui ogni elemento `I` è **func**(( **\*this**)[ `I`]).  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_apply.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
using namespace std;  
  
int __cdecl MyApplyFunc( int n )  
{  
   return n*2;  
}  
  
int main( int argc, char* argv[] )  
{  
   valarray<int> vaR(10), vaApplied(10);  
   int i;  
  
   for ( i = 0; i < 10; i += 3 )  
      vaR[i] = i;  
  
   for ( i = 1; i < 10; i += 3 )  
      vaR[i] = 0;  
  
   for ( i = 2; i < 10; i += 3 )  
      vaR[i] = -i;  
  
   cout << "The initial Right valarray is: (";  
   for   ( i=0; i < 10; ++i )  
      cout << " " << vaR[i];  
   cout << " )" << endl;  
  
   vaApplied = vaR.apply( MyApplyFunc );  
  
   cout << "The element-by-element result of "  
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";  
   for ( i = 0; i < 10; ++i )  
      cout << " " << vaApplied[i];  
   cout << " )" << endl;  
}  
\* Output:   
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )  
The element-by-element result of applying MyApplyFunc to vaR is the  
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )  
*\  
```  
  
##  <a name="cshift"></a>  valarray::cshift  
 Sposta ciclicamente tutti gli elementi in un oggetto valarray in base a un numero specificato di posizioni.  
  
```  
valarray<Type> cshift(int count) const;
```  
  
### <a name="parameters"></a>Parametri  
 `count`  
 Numero di posizioni in base al quale gli elementi devono essere spostati in avanti.  
  
### <a name="return-value"></a>Valore restituito  
 Nuovo oggetto valarray in cui tutti gli elementi sono stati spostati ciclicamente di un numero di posizioni pari a `count` verso l'inizio dell'oggetto valarray, a sinistra rispetto alle relative posizioni nell'operando valarray.  
  
### <a name="remarks"></a>Note  
 Un valore positivo `count` sposta gli elementi ciclicamente verso sinistra di un numero di posizioni pari a `count`.  
  
 Un valore negativo `count` sposta gli elementi ciclicamente verso destra di un numero di posizioni pari a `count`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_cshift.cpp  
// compile with: /EHsc  
  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    valarray<int> va1(10), va2(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
    for (i = 0; i < 10; i+=1)  
        va2[i] = 10 - i;  
  
    cout << "The operand valarray va1 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    // A positive parameter shifts elements right  
    va1 = va1.cshift(4);  
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    cout << "The operand valarray va2 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
  
    // A negative parameter shifts elements left  
    va2 = va2.cshift(-4);  
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
}  
\* Output:   
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)  
The cyclically shifted valarray va1 is:  
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)  
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)  
The cyclically shifted valarray va2 is:  
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)  
*\  
```  
  
##  <a name="free"></a>  valarray::free  
 Libera la memoria usata dall'oggetto valarray.  
  
```  
void free();
```  
  
### <a name="remarks"></a>Note  
 Questa funzione non standard equivale all'assegnazione di un oggetto valarray vuoto. Ad esempio:  
  
```  
valarray<T> v;  
v = valarray<T>();

// equivalent to v.free()  
```  
  
##  <a name="max"></a>  valarray::max  
 Trova l'elemento più grande in un oggetto valarray.  
  
```  
Type max() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Valore massimo degli elementi nell'operando valarray.  
  
### <a name="remarks"></a>Note  
 La funzione membro confronta i valori applicando **operator\<** oppure **operator>** tra coppie di elementi di classe **Type**, per cui devono essere specificati gli operatori per l'elemento **Type**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_max.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MaxValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i - 1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  10 - i;  
  
   cout << "The operand valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MaxValue = vaR.max (  );  
   cout << "The largest element in the valarray is: "  
        << MaxValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).  
The largest element in the valarray is: 13.  
*\  
```  
  
##  <a name="min"></a>  valarray::min  
 Trova l'elemento più piccolo in un oggetto valarray.  
  
```  
Type min() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Valore minimo degli elementi nell'operando valarray.  
  
### <a name="remarks"></a>Note  
 La funzione membro confronta i valori applicando **operator\<** oppure **operator>** tra coppie di elementi di classe **Type**, per cui devono essere specificati gli operatori per l'elemento **Type**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_min.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MinValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  5 - i;  
  
   cout << "The operand valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MinValue = vaR.min ( );  
   cout << "The smallest element in the valarray is: "  
        << MinValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).  
The smallest element in the valarray is: -9.  
*\  
```  
  
##  <a name="op_not"></a>  valarray::operator!  
 Operatore unario che ottiene i valori **NOT** logici di ogni elemento in un oggetto valarray.  
  
```  
valarray<bool> operator!() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray di valori booleani di negazione dei valori degli elementi dell'operando valarray.  
  
### <a name="remarks"></a>Note  
 L'operazione logica **NOT** nega gli elementi perché converte tutti gli zeri in uno e considera tutti i valori diversi da zero come uno e li converte in zeri. L'oggetto valarray restituito di valori booleani è della stessa dimensione dell'operando valarray.  
  
 È inoltre disponibile un oggetto **NOT**[valarray::operator~](#op_dtor) bit per bit di negazione a livello di singoli bit nella rappresentazione binaria di elementi `char` e `int` di un oggetto valarray.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_lognot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<bool> vaNOT ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT = !vaL;  
   cout << "The element-by-element result of "  
        << "the logical NOT operator! is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The element-by-element result of the logical NOT operator! is the  
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="op_mod_eq"></a>  valarray::operator%=  
 Ottiene il resto della divisione degli elementi di una matrice, elemento per elemento, per un oggetto valarray specificato o per un valore del tipo di elemento.  
  
```  
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve dividere, elemento per elemento, l'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray i cui elementi sono il resto della divisione, elemento per elemento, dell'operando valarray in base a `right`  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_class_op_rem.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  53;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -67;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  3*i+1;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL %= vaR;  
   cout << "The remainders from the element-by-element "  
        << "division is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 53 -67 53 -67 53 -67 ).  
The initial  right valarray is: ( 1 4 7 10 13 16 ).  
The remainders from the element-by-element division is the  
 valarray: ( 0 -3 4 -7 1 -3 ).  
*\  
```  
  
##  <a name="and_eq"></a>  valarray::operator&amp;=  
 Ottiene l'operatore **AND** bit per bit di elementi in una matrice con gli elementi corrispondenti in un oggetto valarray specificato o con un valore del tipo di elemento.  
  
```  
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve essere combinato, elemento per elemento, tramite **AND** logico con l'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray i cui elementi sono gli **AND** logici, elemento per elemento, dell'operando valarray divisi in base a `right`  
  
### <a name="remarks"></a>Note  
 È possibile usare un'operazione bit per bit solo per modificare i bit in tipi di dati `char` e `int` e varianti e non per tipi di dati **float**, **double**, **longdouble**, `void`, `bool` o per altri tipi di dati più complessi.  
  
 L'operatore AND bit per bit supporta la stessa tabella di verità dell'operatore **AND** logico, ma si applica al tipo di dati a livello dei singoli bit. Dati i bit *b*1 e *b*2, *b*1 **AND** *b*2 è **true** se entrambi i bit sono true; **false** se almeno uno è false.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_class_op_bitand.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL &= vaR;  
   cout << "The element-by-element result of "  
        << "the logical AND operator&= is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the logical AND operator&= is the  
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).  
*\  
```  
  
##  <a name="op_gt_gt_eq"></a>  valarray::operator&gt;&gt;=  
 Sposta verso destra i bit per ogni elemento di un operando valarray di un numero specificato di posizioni o in base a una quantità di elementi specificata da un secondo oggetto valarray.  
  
```  
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Valore che indica di quanto viene effettuato lo spostamento verso destra oppure oggetto valarray i cui elementi indicano di quanto viene effettuato lo spostamento verso destra elemento per elemento.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray i cui elementi sono stati spostati verso destra in base a quanto specificato in `right`.  
  
### <a name="remarks"></a>Note  
 Per i numeri con segno, i segni vengono mantenuti.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_class_op_rs.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  64;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -64;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL >>= vaR;  
   cout << "The element-by-element result of "  
        << "the right shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the right shift is the  
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).  
*\  
```  
  
##  <a name="op_lt_lt_eq"></a>  valarray::operator&lt;&lt;=  
 Sposta verso sinistra i bit per ogni elemento di un operando valarray di un numero specificato di posizioni o in base a una quantità di elementi specificata da un secondo oggetto valarray.  
  
```  
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Valore che indica di quanto viene effettuato lo spostamento verso sinistra oppure oggetto valarray i cui elementi indicano di quanto viene effettuato lo spostamento verso sinistra elemento per elemento.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray i cui elementi sono stati spostati verso sinistra in base a quanto specificato in `right`.  
  
### <a name="remarks"></a>Note  
 Per i numeri con segno, i segni vengono mantenuti.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_class_op_ls.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL <<= vaR;  
   cout << "The element-by-element result of "  
        << "the left shift\n on the operand array is the valarray:\n ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the left shift  
 on the operand array is the valarray:  
 ( 1 -2 4 -8 16 -32 64 -128 ).  
*\  
```  
  
##  <a name="op_star_eq"></a>  valarray::operator*=  
 Moltiplica gli elementi di un oggetto valarray specificato o un valore del tipo di elemento, elemento per elemento, per un operando valarray.  
  
```  
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve moltiplicare, elemento per elemento, l'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Un oggetto valarray i cui elementi sono il prodotto tra gli elementi dell'oggetto valarray operando e `right`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_emult.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL *= vaR;  
   cout << "The element-by-element result of "  
        << "the multiplication is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the multiplication is the  
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).  
*\  
```  
  
##  <a name="op_add"></a>  valarray::operator+  
 Operatore unario che applica un segno più a ogni elemento in un oggetto valarray.  
  
```  
valarray<Type> operator+() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray i cui elementi sono sommati a quelli dell'operando array.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_eplus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaPLUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaPLUS = +vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaPLUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
*\  
```  
  
##  <a name="op_add_eq"></a>  valarray::operator+=  
 Aggiunge gli elementi di un oggetto valarray specificato o un valore del tipo di elemento, elemento per elemento, a un operando valarray.  
  
```  
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve essere aggiunto, elemento per elemento, all'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Un oggetto valarray i cui elementi sono la somma dell'operando valarray e `right`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_eadd.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL += vaR;  
   cout << "The element-by-element result of "  
        << "the sum is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the sum is the  
 valarray: ( 2 0 4 2 6 4 8 6 ).  
*\  
```  
  
##  <a name="valarray__operator-"></a>  valarray::operator-  
 Operatore unario che applica un segno meno a ogni elemento in un oggetto valarray.  
  
```  
valarray<Type> operator-() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray i cui elementi sono sottratti a quelli dell'operando array.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_eminus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaMINUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaMINUS = -vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaMINUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).  
*\  
```  
  
##  <a name="valarray__operator-_eq"></a>  valarray::operator-=  
 Sottrae gli elementi di un oggetto valarray specificato o un valore del tipo di elemento, elemento per elemento, da un operando valarray.  
  
```  
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve essere sottratto, elemento per elemento, dall'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Un oggetto valarray i cui elementi sono la differenza degli elementi dell'oggetto valarray operando e `right`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_esub.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  10;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL -= vaR;  
   cout << "The element-by-element result of "  
        << "the difference is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the difference is the  
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).  
*\  
```  
  
##  <a name="op_div_eq"></a>  valarray::operator/=  
 Divide un operando valarray, elemento per elemento, per gli elementi di un oggetto valarray specificato o per un valore del tipo di elemento.  
  
```  
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve essere diviso, elemento per elemento, per l'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Un oggetto valarray i cui elementi sono il quoziente dell'operando valarray diviso `right`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_ediv.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<double> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  100;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -100;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  2*i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL /= vaR;  
   cout << "The element-by-element result of "  
        << "the quotient is the\n valarray: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 100 -100 100 -100 100 -100 ).  
The initial Right valarray is: ( 0 2 4 6 8 10 ).  
The element-by-element result of the quotient is the  
 valarray: ( 1.#INF -50 25 -16.6667 12.5 -10 ).  
*\  
```  
  
##  <a name="op_eq"></a>  valarray::operator=  
 Assegna elementi a un oggetto valarray i cui valori vengono specificati direttamente, come parte di altri oggetti valarray oppure tramite slice_array, gslice_array, mask_array o indirect_array.  
  
```  
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray da copiare nell'operando valarray.  
  
 `val`  
 Valore da assegnare agli elementi dell'operando valarray.  
  
 `_Slicearray`  
 Oggetto slice_array da copiare nell'operando valarray.  
  
 `_Gslicearray`  
 Oggetto gslice_array da copiare nell'operando valarray.  
  
 `_Maskarray`  
 Oggetto mask_array da copiare nell'operando valarray.  
  
 `_Indarray`  
 Oggetto indirect_array da copiare nell'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Il primo operatore membro sostituisce la sequenza controllata con una copia della sequenza controllata da `right`.  
  
 Il secondo operatore membro è uguale al primo, ma con un [dichiaratore di riferimento rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 Il terzo operatore membro sostituisce ogni elemento della sequenza controllata con una copia di `val`.  
  
 Gli operatori membro restanti sostituiscono gli elementi della sequenza controllata selezionati dai relativi argomenti, che vengono generati solo da [operator&#91;&#93;](#op_at).  
  
 Se il valore di un membro nella sequenza controllata di sostituzioni dipende da un membro nella sequenza controllata iniziale, il risultato è indefinito.  
  
### <a name="remarks"></a>Note  
 Se la lunghezza della sequenza controllata cambia, il risultato è in genere indefinito. In questa implementazione tuttavia l'effetto è semplicemente quello di invalidare eventuali puntatori o riferimenti a elementi nella sequenza controllata.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_assign.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va [ i ] = i;  
   for ( i = 0 ; i < 10 ; i+=1 )  
      vaR [ i ] = 10 -  i;  
  
   cout << "The operand valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   cout << "The operand valarray vaR is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << vaR [ i ];  
   cout << endl;  
  
   // Assigning vaR to va with the first member functon  
   va = vaR;  
   cout << "The reassigned valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   // Assigning elements of value 10 to va  
   // with the second member functon  
   va = 10;  
   cout << "The reassigned valarray va is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << va [ i ];  
   cout << endl;  
}  
\* Output:   
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9  
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10  
*\  
```  
  
##  <a name="op_at"></a>  valarray::operator[]  
 Restituisce un riferimento a un elemento o al relativo valore in corrispondenza di un indice o un subset specificato.  
  
```  
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

 
valarray<Type> operator[](slice _Slice) const;

 
valarray<Type> operator[](const gslice& _Gslicearray) const;

 
valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

 
valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```  
  
### <a name="parameters"></a>Parametri  
 `_Off`  
 Indice dell'elemento a cui deve essere assegnato un valore.  
  
 `_Slicearray`  
 Oggetto slice_array di un oggetto valarray che specifica un subset che deve essere selezionato o restituito a un nuovo oggetto valarray.  
  
 `_Gslicearray`  
 Oggetto gslice_array di un oggetto valarray che specifica un subset che deve essere selezionato o restituito a un nuovo oggetto valarray.  
  
 *_Boolarray*  
 Oggetto bool_array di un oggetto valarray che specifica un subset che deve essere selezionato o restituito a un nuovo oggetto valarray.  
  
 `_Indarray`  
 Oggetto indirect_array di un oggetto valarray che specifica un subset che deve essere selezionato o restituito a un nuovo oggetto valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Riferimento a un elemento o al relativo valore in corrispondenza di un indice o un subset specificato.  
  
### <a name="remarks"></a>Note  
 L'operatore membro è sottoposto a overload per fornire diversi modi per selezionare sequenze di elementi tra quelle controllate da *\****this**. Il primo gruppo di cinque operatori membro funziona insieme a diversi overload di [operator=](#op_eq) (e altri operatori di assegnazione) per consentire la sostituzione selettiva (sezionamento) della sequenza controllata. Gli elementi selezionati devono esistere.  
  
 Durante la compilazione tramite [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definito come 1 o 2, si verificherà un errore di runtime se si tenta di accedere a un elemento non incluso nei limiti dell'oggetto valarray.  Per altre informazioni, vedere [Iteratori verificati](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Esempio  
  Per un esempio su come dichiarare e usare l'operatore, vedere gli esempi per [slice::slice](../standard-library/slice-class.md#slice) e [gslice::gslice](../standard-library/gslice-class.md#gslice).  
  
##  <a name="op_xor_eq"></a>  valarray::operator^=  
 Ottiene l'operatore OR logico esclusivo elemento per elemento (**XOR**) di una matrice con un oggetto valarray specificato o un valore del tipo di elemento.  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve essere combinato, elemento per elemento, tramite **XOR** logico esclusivo con l'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Un oggetto valarray i cui elementi sono logico esclusivo elemento per elemento, **XOR** dell'operando valarray e `right`.  
  
### <a name="remarks"></a>Note  
 L'operatore or logico esclusivo, indicato come **XOR**, supporta la semantica seguente: dati gli elementi *e*1 e *e*2, *e*1 **XOR** *e*2 è **true** se uno degli elementi è true; **false** se entrambi gli elementi sono false o se entrambi gli elementi sono true.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_exor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL ^= vaR;  
   cout << "The element-by-element result of "  
        << "the bitwise XOR operator^= is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise XOR operator^= is the  
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).  
*\  
```  
  
##  <a name="op_or_eq"></a>  valarray::operator&#124;=  
 Ottiene l'operatore `OR` bit per bit di elementi in una matrice con gli elementi corrispondenti in un oggetto valarray specificato o con un valore del tipo di elemento.  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Oggetto valarray o valore di un tipo di elemento identico a quello dell'operando valarray che deve essere combinato, elemento per elemento, tramite `OR` bit per bit con l'operando valarray.  
  
### <a name="return-value"></a>Valore restituito  
 Un oggetto valarray i cui elementi sono l'elemento per elemento or `OR` dell'operando valarray da `right`.  
  
### <a name="remarks"></a>Note  
 È possibile usare un'operazione bit per bit solo per modificare i bit in tipi di dati `char` e `int` e varianti e non per tipi di dati **float**, **double**, **longdouble**, `void`, `bool` o per altri tipi di dati più complessi.  
  
 L'operatore `OR` bit per bit supporta la stessa tabella di verità dell'operatore `OR` logico, ma si applica al tipo di dati a livello dei singoli bit. Dati i bit *b*1 e *b*2, *b*1 `OR` *b*2 è **true** se almeno uno dei bit è true; **false** se entrambi i bit sono false.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_class_op_bitor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial operand valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL |= vaR;  
   cout << "The element-by-element result of "  
        << "the logical OR\n operator|= is the valarray:\n ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  
 ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is:  
 ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the logical OR  
 operator|= is the valarray:  
 ( 1 0 1 3 3 4 7 6 7 9 ).  
*\  
```  
  
##  <a name="op_dtor"></a>  valarray::operator~  
 Operatore unario che ottiene i valori **NOT** bit per bit di ogni elemento in un oggetto valarray.  
  
```  
valarray<Type> operator~() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto valarray di valori booleani che sono gli operatori **NOT** bit per bit dei valori degli elementi dell'operando valarray.  
  
### <a name="remarks"></a>Note  
 È possibile usare un'operazione bit per bit solo per modificare i bit in tipi di dati `char` e `int` e varianti e non per tipi di dati **float**, **double**, **longdouble**, `void`, `bool` o per altri tipi di dati più complessi.  
  
 L'operatore **NOT** bit per bit supporta la stessa tabella di verità dell'operatore **NOT** logico, ma si applica al tipo di dati a livello dei singoli bit. Dato il bit *b*, ~ *b* è true se *b* è false e false se *b* è true. L'operatore **NOT**[operator!](#op_not) logico si applica a livello di elemento, conteggiando tutti i valori diversi da zero come **true** e il risultato è un oggetto valarray di valori booleani. L'operatore **NOToperator~** bit per bit invece può determinare un oggetto valarray di valori diversi da 0 o 1, a seconda del risultato dell'operazione bit per bit.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_op_bitnot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<unsigned short int> vaL1 ( 10 );  
   valarray<unsigned short int> vaNOT1 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  5*i;  
  
   cout << "The initial valarray <unsigned short int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL1 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT1 = ~vaL1;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT1 [ i ] << " ";  
   cout << ")." << endl << endl;  
  
   valarray<int> vaL2 ( 10 );  
   valarray<int> vaNOT2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  -2 * i;  
  
   cout << "The initial valarray <int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL2 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT2 = ~vaL2;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // The negative numbers are represented using  
   // the two's complement approach, so adding one  
   // to the flipped bits returns the negative elements  
   vaNOT2 = vaNOT2 + 1;  
   cout << "The element-by-element result of "  
        << "adding one\n is the negative of the "  
        << "original elements the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).  
  
The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).  
The element-by-element result of adding one  
 is the negative of the original elements the  
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).  
*\  
```  
  
##  <a name="resize"></a>  valarray::resize  
 Modifica il numero di elementi in un oggetto valarray in un numero specificato.  
  
```  
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,   
    const Type val);
```  
  
### <a name="parameters"></a>Parametri  
 `_Newsize`  
 Il numero di elementi nell'oggetto valarray ridimensionato.  
  
 `val`  
 Il valore da assegnare agli elementi dell'oggetto valarray ridimensionato.  
  
### <a name="remarks"></a>Note  
 La prima funzione membro inizializza gli elementi con il costruttore predefinito.  
  
 Eventuali puntatori o riferimenti agli elementi nella sequenza controllata vengono invalidati.  
  
### <a name="example"></a>Esempio  
  L'esempio seguente illustra l'uso della funzione membro valarray::resize.  
  
```  
// valarray_resize.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, sizeNew;  
  
    valarray<int> va1(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray is: "  
         << size1  << "." <<endl << endl;  
  
    va1.resize(15, 10);  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 15; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
    sizeNew = va1.size();  
    cout << "The number of elements in the resized valarray is: "  
         << sizeNew  << "." <<endl << endl;  
}  
\* Output:   
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray is: 10.  
  
The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).  
The number of elements in the resized valarray is: 15.  
*\  
```  
  
##  <a name="shift"></a>  valarray::shift  
 Sposta tutti gli elementi in un oggetto valarray in base a un numero specificato di posizioni.  
  
```  
valarray<Type> shift(int count) const;
```  
  
### <a name="parameters"></a>Parametri  
 `count`  
 Numero di posizioni in base al quale gli elementi devono essere spostati in avanti.  
  
### <a name="return-value"></a>Valore restituito  
 Nuovo oggetto valarray in cui tutti gli elementi sono stati spostati di un numero di posizioni pari a `count` verso l'inizio dell'oggetto valarray, a sinistra rispetto alle relative posizioni nell'operando valarray.  
  
### <a name="remarks"></a>Note  
 Un valore positivo `count` sposta gli elementi verso sinistra di un numero di posizioni pari a `count`, con riempimento zero.  
  
 Un valore negativo `count` sposta gli elementi verso destra di un numero di posizioni pari a `count`, con riempimento zero.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_shift.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va1 ( 10 ), va2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va1 [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va2 [ i ] = 10 -  i;  
  
   cout << "The operand valarray va1(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A positive parameter shifts elements left  
   va1 = va1.shift ( 4 );  
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The operand valarray va2(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A negative parameter shifts elements right  
   va2 = va2.shift ( - 4 );  
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).  
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).  
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).  
*\  
```  
  
##  <a name="size"></a>  valarray::size  
 Trova il numero di elementi in un oggetto valarray.  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di elementi nell'operando valarray.  
  
### <a name="example"></a>Esempio  
  L'esempio seguente illustra l'uso della funzione membro valarray::size.  
  
```  
// valarray_size.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, size2;  
  
    valarray<int> va1(10), va2(12);  
    for (i = 0; i < 10; i += 1)  
        va1[i] =  i;  
    for (i = 0; i < 10; i += 1)  
        va2[i] =  i;  
  
    cout << "The operand valarray va1(10) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray va1 is: va1.size = "  
         << size1  << "." <<endl << endl;  
  
    cout << "The operand valarray va2(12) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
  
    size2 = va2.size();  
    cout << "The number of elements in the valarray va2 is: va2.size = "  
         << size2  << "." << endl << endl;  
  
    // Initializing two more elements to va2  
    va2[10] = 10;  
    va2[11] = 11;  
    cout << "After initializing two more elements,\n "  
         << "the operand valarray va2(12) is now: ( ";  
        for (i = 0; i < 12; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
    cout << "The number of elements in the valarray va2 is still: "  
         << size2  << "." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va1 is: va1.size = 10.  
  
The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va2 is: va2.size = 12.  
  
After initializing two more elements,  
 the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).  
The number of elements in the valarray va2 is still: 12.  
*\  
```  
  
##  <a name="sum"></a>  valarray::sum  
 Determina la somma di tutti gli elementi in un oggetto valarray di lunghezza diversa da zero.  
  
```  
Type sum() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Somma degli elementi dell'operando valarray.  
  
### <a name="remarks"></a>Note  
 Se la lunghezza è maggiore di uno, la funzione membro aggiunge valori alla somma applicando `operator+=` tra coppie di elementi di classe **Type**, operatore che, di conseguenza, deve essere specificato per gli elementi di tipo **Type**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_sum.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   int sumva = 0;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i+=1 )  
      va [ i ] =  i;  
  
   cout << "The operand valarray va (10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   sumva = va.sum ( );  
   cout << "The sum of elements in the valarray is: "  
        << sumva  << "." <<endl;  
}  
\* Output:   
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The sum of elements in the valarray is: 45.  
*\  
```  
  
##  <a name="swap"></a>  valarray::swap  
 Scambia gli elementi di due `valarray`.  
  
```  
void swap(valarray& right);
```  
  
### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`right`|Oggetto `valarray` che fornisce gli elementi da scambiare.|  
  
### <a name="remarks"></a>Note  
 La funzione membro scambia le sequenze controllate tra `*this` e `right`. Esegue l'operazione in un tempo costante, non genera alcuna eccezione e non invalida alcun riferimento, puntatore o gli iteratori che definiscono gli elementi nelle due sequenze controllate.  
  
##  <a name="valarray"></a>  valarray::valarray  
 Costruisce un oggetto valarray con una dimensione specifica, con gli elementi di un valore specifico, come una copia di un altro oggetto valarray o come sottoinsieme di un altro valarray.  
  
```  
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,   
    size_t Count);

valarray(
    const Type* Ptr,   
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```  
  
### <a name="parameters"></a>Parametri  
 `Count`  
 Numero di elementi che possono essere contenuti in un oggetto valarray.  
  
 `Val`  
 Valore da utilizzare durante l'inizializzazione degli elementi nell'oggetto valarray.  
  
 `Ptr`  
 Puntatore ai valori da utilizzare per inizializzare gli elementi nell'oggetto valarray.  
  
 `Right`  
 Oggetto valarray già esistente per inizializzare il nuovo oggetto valarray.  
  
 `SliceArray`  
 Oggetto slice_array i cui valori degli elementi devono essere utilizzati durante l'inizializzazione degli elementi dell'oggetto valarray costruito.  
  
 `GsliceArray`  
 Oggetto gslice_array i cui valori degli elementi devono essere utilizzati durante l'inizializzazione degli elementi dell'oggetto valarray costruito.  
  
 `MaskArray`  
 Oggetto mask_array i cui valori degli elementi devono essere utilizzati durante l'inizializzazione degli elementi dell'oggetto valarray costruito.  
  
 `IndArray`  
 Oggetto indirect_array i cui valori degli elementi devono essere utilizzati durante l'inizializzazione degli elementi dell'oggetto valarray costruito.  
  
 `IList`  
 Oggetto initializer_list contenente gli elementi da copiare.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore (predefinito) inizializza l'oggetto a una matrice vuota. Tre costruttori successivi che inizializzano l'oggetto a una matrice di elementi `Count` come segue:  
  
-   Per un oggetto `valarray(size_t Count)` esplicito, ogni elemento viene inizializzato con un costruttore predefinito.  
  
-   Per `valarray(const Type& Val, Count)`, ogni elemento viene inizializzato con `Val`.  
  
-   Per `valarray(const Type* Ptr, Count)`, l'elemento nella posizione `I` viene inizializzato con `Ptr`[ `I`].  
  
 Ogni costruttore rimanente inizializza l'oggetto in un oggetto valarray\<Type> determinato dal subset specificato nell'argomento.  
  
 L'ultimo costruttore è lo stesso di quello accanto all'ultimo, ma con un [dichiaratore di riferimento rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_ctor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    // The second member function  
    valarray<int> va(10);  
    for (auto i : va){  
        va[i] = 2 * (i + 1);  
    }  
  
    cout << "The operand valarray va is:\n(";  
    for (auto i : va) {  
        cout << " " << va[i];  
    }  
    cout << " )" << endl;  
  
    slice Slice(2, 4, 3);  
  
    // The fifth member function  
    valarray<int> vaSlice = va[Slice];  
  
    cout << "The new valarray initialized from the slice is vaSlice ="  
        << "\nva[slice( 2, 4, 3)] = (";  
    for (int i = 0; i < 3; i++) {  
        cout << " " << vaSlice[i];  
    }  
    cout << " )" << endl;  
  
    valarray<int> va2{{ 1, 2, 3, 4 }};  
    for (auto& v : va2){  
        cout << v << " ";  
    }  
    cout << endl;  
}  
  
```  
  
```Output  
The operand valarray va is:( 0 2 2 2 2 2 2 2 2 2 )The new valarray initialized from the slice is vaSlice =va[slice( 2, 4, 3)] = ( 0 0 0 )1 2 3 4  
```  
  
##  <a name="value_type"></a>  valarray::value_type  
 Tipo che rappresenta il tipo di elemento archiviato in un oggetto valarray.  
  
```  
typedef Type value_type;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo del parametro di modello **Type**.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// valarray_value_type.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // value_type declaration and initialization:  
   valarray<int>::value_type Right = 10;  
  
   cout << "The decalared value_type Right is: "   
           << Right << endl;  
   va *= Right;  
   cout << "The resulting valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The decalared value_type Right is: 10  
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).  
*\  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Thread Safety in the C++ Standard Library](../standard-library/thread-safety-in-the-cpp-standard-library.md) (Thread safety nella libreria standard C++)

