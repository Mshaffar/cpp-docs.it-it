---
title: Classe is_union | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_union
dev_langs: C++
helpviewer_keywords:
- is_union class
- is_union
ms.assetid: 80eda256-40b8-4db5-9ac1-d58bb8032a3e
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bb37e6aa3b43bcf1fdd99f3286962749fbdf12fa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="isunion-class"></a>Classe is_union
Verifica se il tipo è un'unione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
template <class Ty>  
struct is_union;  
```  
  
#### <a name="parameters"></a>Parametri  
 `Ty`  
 Tipo su cui eseguire una query.  
  
## <a name="remarks"></a>Note  
 Un'istanza del predicato di tipo contiene true se il tipo `Ty` è un tipo di unione o un form `cv-qualified` di un tipo di unione; in caso contrario, contiene false.  
  
## <a name="example"></a>Esempio  
  
```cpp  
// std__type_traits__is_union.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
union ints   
    {   
    int in;   
    long lo;   
    };   
  
int main()   
    {   
    std::cout << "is_union<trivial> == " << std::boolalpha   
        << std::is_union<trivial>::value << std::endl;   
    std::cout << "is_union<int> == " << std::boolalpha   
        << std::is_union<int>::value << std::endl;   
    std::cout << "is_union<ints> == " << std::boolalpha   
        << std::is_union<ints>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_union<trivial> == false  
is_union<int> == false  
is_union<ints> == true  
```  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<type_traits>  
  
 **Spazio dei nomi:** std  
  
## <a name="see-also"></a>Vedere anche  
 [<type_traits>](../standard-library/type-traits.md)   
 [Classe is_class](../standard-library/is-class-class.md)