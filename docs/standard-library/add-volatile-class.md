---
title: Classe add_volatile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::add_volatile
dev_langs: C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a761257067299615cf7191b22ba45abc03fcd256
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="addvolatile-class"></a>Classe add_volatile
Crea un tipo volatile dal tipo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
template <class Ty>  
struct add_volatile;  
 
template <class T>
using add_volatile_t = typename add_volatile<T>::type;  
```  
  
### <a name="parameters"></a>Parametri  
*T*  
Tipo da modificare.  
  
## <a name="remarks"></a>Note  
Un'istanza di `add_volatile<T>` ha un typedef del membro `type` che è *T* se *T* è un riferimento, una funzione o un tipo qualificato volatile. In caso contrario sarà `volatile` *T*. L'alias `add_volatile_t` è un collegamento per l'accesso al typedef del membro `type`. 
  
## <a name="example"></a>Esempio  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_volatile_t<int> *p = (volatile int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_volatile<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
} 
```  
  
```Output  
add_volatile<int> == int  
```  
  
## <a name="requirements"></a>Requisiti  

**Intestazione:** \<type_traits>  
  
**Spazio dei nomi:** std  
  
## <a name="see-also"></a>Vedere anche  
[<type_traits>](../standard-library/type-traits.md)   
[Classe remove_volatile](../standard-library/remove-volatile-class.md)