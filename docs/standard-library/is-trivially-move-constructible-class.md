---
title: Classe is_trivially_move_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 279da956eaff21c39c6e5ca563f26989105f7e74
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448366"
---
# <a name="istriviallymoveconstructible-class"></a>Classe is_trivially_move_constructible

Verifica se il tipo ha un costruttore di spostamento semplice.

## <a name="syntax"></a>Sintassi

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametri

*Ty*\
Tipo su cui eseguire una query.

## <a name="remarks"></a>Note

Un'istanza del predicato di tipo contiene true se il tipo *Ty* è una classe che ha un costruttore di spostamento semplice; in caso contrario, contiene false.

Un costruttore di spostamento per una classe *Ty* è semplice se:

viene dichiarato in modo implicito

i tipi di parametro sono equivalenti a quelli di una dichiarazione implicita

la classe *Ty* non ha funzioni virtuali

la classe *Ty* non ha basi virtuali

la classe non ha alcun membro dati non statici volatili

tutte le basi dirette della classe *Ty* hanno costruttori di spostamento semplici

le classi di tutti i membri dati non statici del tipo di classe hanno costruttori di spostamento semplici

le classi di tutti i membri dati non statici di tipo matrice della classe hanno costruttori di spostamento semplici

## <a name="requirements"></a>Requisiti

**Intestazione:** \<type_traits>

**Spazio dei nomi:** std

## <a name="see-also"></a>Vedere anche

[<type_traits>](../standard-library/type-traits.md)
