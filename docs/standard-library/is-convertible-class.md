---
title: Classe is_convertible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_convertible
helpviewer_keywords:
- is_convertible class
- is_convertible
ms.assetid: 75614008-1894-42ea-bd57-974399628536
ms.openlocfilehash: c90fe5687992e4df49e8655387cfdd14b40aa529
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454615"
---
# <a name="isconvertible-class"></a>Classe is_convertible

Verifica se il tipo è convertibile in un altro tipo.

## <a name="syntax"></a>Sintassi

```cpp
template <class From, class To>
struct is_convertible;
```

### <a name="parameters"></a>Parametri

*Da*\
Tipo da cui eseguire la conversione.

*Ty*\
Tipo in cui eseguire la conversione.

## <a name="remarks"></a>Note

Un'istanza del tipo predicato contiene true se l'espressione `To to = from;`, dove `from` è un oggetto di tipo `From`, è in formato corretto.

## <a name="example"></a>Esempio

```cpp
// std__type_traits__is_convertible.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha
        << std::is_convertible<trivial, int>::value << std::endl;
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha
        << std::is_convertible<trivial, trivial>::value << std::endl;
    std::cout << "is_convertible<char, int> == " << std::boolalpha
        << std::is_convertible<char, int>::value << std::endl;

    return (0);
    }
```

```Output
is_convertible<trivial, int> == false
is_convertible<trivial, trivial> == true
is_convertible<char, int> == true
```

## <a name="requirements"></a>Requisiti

**Intestazione:** \<type_traits>

**Spazio dei nomi:** std

## <a name="see-also"></a>Vedere anche

[<type_traits>](../standard-library/type-traits.md)\
[Classe is_base_of](../standard-library/is-base-of-class.md)
