---
title: Struct modulus | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- modulus
- xfunctional/std::modulus
dev_langs:
- C++
helpviewer_keywords:
- modulus class
- modulus struct
ms.assetid: 86d342f7-b7b1-46a4-b0bb-6b7ae827369b
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 430f1f9c0fcc58e3b4bfef167356960eb132b3f7
ms.lasthandoff: 02/24/2017

---
# <a name="modulus-struct"></a>Struct modulus
Oggetto funzione predefinito che esegue l'operazione di divisione modulo ( `operator%`) negli argomenti.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class Type = void>
struct modulus : public binary_function <Type, Type, Type>  
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator%
template <>
struct modulus<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) % std::forward<U>(Right));
};
```  
  
#### <a name="parameters"></a>Parametri  
 `Type`, `T`, `U`  
 Qualsiasi tipo che supporta un `operator%` che accetta gli operandi dei tipi specificati o dedotti.  
  
 `Left`  
 Operando sinistro dell'operazione modulo. Il modello non specializzato accetta un argomento di riferimento lvalue di tipo `Type`. Il modello specializzato esegue un inoltro perfetto degli argomenti di riferimento lvalue e rvalue del tipo dedotto `T`.  
  
 `Right`  
 Operando destro dell'operazione modulo. Il modello non specializzato accetta un argomento di riferimento lvalue di tipo `Type`. Il modello specializzato esegue un inoltro perfetto degli argomenti di riferimento lvalue e rvalue del tipo dedotto `U`.  
  
## <a name="return-value"></a>Valore restituito  
 Risultato di `Left``%``Right`. Il modello specializzato esegue un inoltro perfetto del risultato, con il tipo restituito da `operator%`.  
  
## <a name="remarks"></a>Note  
 Il funtore `modulus` è limitato ai tipi integrali per i tipi di dati di base o ai tipi definiti dall'utente che implementano `operator%`.  
  
## <a name="example"></a>Esempio  
  
```cpp  
// functional_modulus.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <int> v1, v2, v3 ( 6 );  
   vector <int>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 1 ; i <= 6 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   int j;  
   for ( j = 1 ; j <= 6 ; j++ )  
   {  
      v2.push_back( 3 * j );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise remainders of the elements of v1 & v2  
   transform (v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      modulus<int>() );  
  
   cout << "The element-wise remainders of the modular division\n are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
/* Output:  
The vector v1 = ( 5 10 15 20 25 30 )  
The vector v2 = ( 3 6 9 12 15 18 )  
The element-wise remainders of the modular division  
 are: ( 2 4 6 8 10 12 )  
 */  
```  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<functional>  
  
 **Spazio dei nomi:** std  
  
## <a name="see-also"></a>Vedere anche  
 [Thread Safety in the C++ Standard Library](../standard-library/thread-safety-in-the-cpp-standard-library.md)  (Sicurezza dei thread nella libreria standard C++)  
 [Riferimento per la libreria standard C++](../standard-library/cpp-standard-library-reference.md)



