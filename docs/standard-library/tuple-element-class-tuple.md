---
title: Classe tuple_element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple_element
- std::tuple_element
- utility/std::tuple_element
dev_langs:
- C++
helpviewer_keywords:
- tuple_element Class
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: aadbf7d2c6fece48ab29c1b818995464a790c38b
ms.openlocfilehash: b5568eb951738b1c0c53321d7430c84db6bac9ec
ms.contentlocale: it-it
ms.lasthandoff: 03/07/2017

---
# <a name="tupleelement-class"></a>Classe tuple_element
Esegue il wrapping di un elemento `tuple` . Le specializzazioni eseguono il wrapping di elementi `array` e `pair`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
// CLASS tuple_element (find element by index)  
template <size_t Index, class Tuple>  
   struct tuple_element;  
 
// tuple_element for const 
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const Tuple>;  
 
// tuple_element for volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, volatile Tuple>;  
 
// tuple_element for const volatile  
template <size_t Index, class Tuple>  
   struct tuple_element<Index, const volatile Tuple>;  
 
// Helper typedef
template <size_t Index, class Tuple>  
   using tuple_element_t = typename tuple_element<Index, Tuple>::type; 

// Specialization for arrays  
template <size_t Index, class Elem, size_t Size>  
   struct tuple_element<Index, array<Elem, Size>>;  
  
// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```  
  
### <a name="parameters"></a>Parametri  
*Index*  
Indice dell'elemento designato.  
  
*Tuple*  
Tipo della tupla.  
  
*Elem*  
Tipo di un elemento della matrice.  
  
*Size*  
Dimensione della matrice.  

*T1* Tipo del primo elemento di una coppia.
  
*T2*  
Tipo del secondo elemento di una coppia.

## <a name="remarks"></a>Note  
La classe modello `tuple_element` include un typedef annidato `type` che è sinonimo del tipo in corrispondenza dell'indice `Index` del tipo di tupla `Tuple`.  

Il typedef `tuple_element_t` è un alias conveniente per `tuple_element<Index, Tuple>::type`.  
  
La specializzazione della classe modello per le matrici fornisce un'interfaccia a un oggetto `array` come tupla di `Size` elementi, ognuno dei quali è dello stesso tipo. Ogni specializzazione dispone di un typedef annidato `type` che è un sinonimo del tipo dell'elemento `Index` di `array`, con qualsiasi qualificazione const-volatile mantenuta.  
  
Le specializzazioni modello per i tipi `pair` forniscono ciascuna un singolo membro typedef, `type`, che è un sinonimo del tipo di elemento in corrispondenza della posizione specificata nella coppia, con qualsiasi qualificazione const e/o volatile mantenuta. Il typedef `tuple_element_t` è un alias conveniente per `tuple_element<N, pair<T1, T2>>::type`.  
  
Utilizzare il [funzione get &lt;utilità&gt; ](../standard-library/utility-functions.md#get) per restituire l'elemento in una posizione specificata, o di un tipo specificato. 
  
## <a name="example"></a>Esempio  
  
```cpp  
#include <tuple>  
#include <string>  
#include <iostream>  
  
using namespace std;  
typedef tuple<int, double, string> MyTuple;  
  
int main() {  
    MyTuple c0{ 0, 1.5, "Tail" };  
  
    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index  
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);  
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type  
  
    cout << val << " " << val2 << " " << val3 << endl;  
}  
```  
  
```Output  
0 1.5 Tail  
```  
  
## <a name="example"></a>Esempio  
  
```cpp  
#include <array>   
#include <iostream>   
  
using namespace std;  
typedef array<int, 4> MyArray;  
  
int main()  
{  
    MyArray c0 { 0, 1, 2, 3 };  
  
    for (const auto& e : c0)  
    {  
        cout << " " << e;  
    }  
    cout << endl;  
  
    // display first element " 0"   
    tuple_element<0, MyArray>::type val = c0.front();  
    cout << " " << val << endl;  
}  
```  
  
```Output  
 0 1 2 3  
 0  
```  
  
## <a name="example"></a>Esempio  
  
```cpp  
#include <utility>   
#include <iostream>   
  
using namespace std;  
  
typedef pair<int, double> MyPair;  
int main() {  
    MyPair c0(0, 1.333);  
  
    // display contents " 0 1"   
    cout << " " << get<0>(c0);  
    cout << " " << get<1>(c0) << endl;  
  
    // display first element " 0" by index  
    tuple_element<0, MyPair>::type val = get<0>(c0);  
    cout << " " << val;  
  
    // display second element by type   
    tuple_element<1, MyPair>::type val2 = get<double>(c0);  
    cout << " " << val2 << endl;  
}  
```  
  
```Output  
 0 1.333  
 0 1.333  
```  

## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<tuple>  
 **Intestazione:** \<array> (per la specializzazione di matrice)  **Intestazione:** \<utility> (per le specializzazioni di coppia)  **Spazio dei nomi:** std  
  
## <a name="see-also"></a>Vedere anche  
[tuple ](../standard-library/tuple-class.md)
