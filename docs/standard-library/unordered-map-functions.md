---
title: Funzioni &lt;unordered_map&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unordered_map/std::swap
- unordered_map/std::swap (unordered_map)
- unordered_map/std::swap (unordered_multimap)
dev_langs:
- C++
ms.assetid: cf2e4115-f205-4a0e-90be-a143ffcc1f44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: b60954085c747fb06bc6ba4f6058909a54765e49
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="ltunorderedmapgt-functions"></a>Funzioni &lt;unordered_map&gt;
|||  
|-|-|  
|[swap (unordered_map)](#swap)|[swap (unordered_multimap)](#swap_function_multimap)|  
  
##  <a name="swap"></a>  swap (unordered_map)  
 Scambia il contenuto di due contenitori.  
  
```  
template <class Key, class Ty, class Hash, class Pred, class Alloc>  
void swap(
    unordered_map <Key, Ty, Hash, Pred, Alloc>& left,  
    unordered_map <Key, Ty, Hash, Pred, Alloc>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `Key`  
 Tipo di chiave.  
  
 `Ty`  
 Tipo mappato.  
  
 `Hash`  
 Tipo di oggetto della funzione hash.  
  
 `Pred`  
 Tipo di oggetto della funzione di confronto di uguaglianza.  
  
 `Alloc`  
 Classe Allocator.  
  
 `left`  
 Primo contenitore da scambiare.  
  
 `right`  
 Secondo contenitore da scambiare.  
  
### <a name="remarks"></a>Note  
 La funzione modello esegue `left.`[unordered_map::swap](../standard-library/unordered-map-class.md#swap)`(right)`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__unordered_map__u_m_swap.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_map<char, int> Mymap;   
int main()   
    {   
    Mymap c1;   
  
    c1.insert(Mymap::value_type('a', 1));   
    c1.insert(Mymap::value_type('b', 2));   
    c1.insert(Mymap::value_type('c', 3));   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    Mymap c2;   
  
    c2.insert(Mymap::value_type('d', 4));   
    c2.insert(Mymap::value_type('e', 5));   
    c2.insert(Mymap::value_type('f', 6));   
  
    c1.swap(c2);   
  
// display contents " [f 6] [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    swap(c1, c2);   
  
// display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();   
        it != c1.end(); ++it)   
        std::cout << " [" << it->first << ", " << it->second << "]";   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[f, 6] [e, 5] [d, 4]  
[c, 3] [b, 2] [a, 1]  
```  
  
##  <a name="swap_function_multimap"></a>  swap (unordered_multimap)  
 Scambia il contenuto di due contenitori.  
  
```  
template <class Key, class Ty, class Hash, class Pred, class Alloc>  
void swap(
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& left,  
    unordered_multimap <Key, Ty, Hash, Pred, Alloc>& right);
```  
  
### <a name="parameters"></a>Parametri  
 `Key`  
 Tipo di chiave.  
  
 `Ty`  
 Tipo mappato.  
  
 `Hash`  
 Tipo di oggetto della funzione hash.  
  
 `Pred`  
 Tipo di oggetto della funzione di confronto di uguaglianza.  
  
 `Alloc`  
 Classe Allocator.  
  
 `left`  
 Primo contenitore da scambiare.  
  
 `right`  
 Secondo contenitore da scambiare.  
  
### <a name="remarks"></a>Note  
 La funzione modello esegue `left.`[unordered_multimap::swap](../standard-library/unordered-multimap-class.md#swap)`(right)`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__unordered_map__u_mm_swap.cpp   
// compile with: /EHsc   
#include <unordered_map>   
#include <iostream>   
  
typedef std::unordered_multimap<char, int> Mymap;
int main()
{
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    Mymap c2;

    c2.insert(Mymap::value_type('d', 4));
    c2.insert(Mymap::value_type('e', 5));
    c2.insert(Mymap::value_type('f', 6));

    c1.swap(c2);

    // display contents " [f 6] [e 5] [d 4]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c 3] [b 2] [a 1]"   
    for (Mymap::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << it->first << ", " << it->second << "]";
    std::cout << std::endl;

    return (0);
}
  
```  
  
```Output  
[c, 3] [b, 2] [a, 1]  
[f, 6] [e, 5] [d, 4]  
[c, 3] [b, 2] [a, 1]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [<unordered_map>](../standard-library/unordered-map.md)

