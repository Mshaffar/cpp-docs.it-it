---
title: requires_category (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: 19a454a8bfc959d7d97959d765dbf68d0f766ca1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214552"
---
# <a name="requires_category"></a>requires_category

Specifica le categorie di componenti obbligatorie della classe di destinazione.

## <a name="syntax"></a>Sintassi

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Parametri

*requires_category*<br/>
ID della categoria richiesta.

## <a name="remarks"></a>Osservazioni

L'attributo **requires_category** C++ specifica le categorie di componenti richieste dalla classe di destinazione. Per ulteriori informazioni, vedere [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Questo attributo richiede che anche l'attributo [coclass](coclass.md), [progid](progid.md)o [vi_progid](vi-progid.md) (o un altro attributo che implica uno di questi) sia applicato allo stesso elemento.

## <a name="example"></a>Esempio

Il codice seguente richiede che l'oggetto implementi la categoria del controllo.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**|
|**Ripetibile**|No|
|**Attributi obbligatori**|Uno o più degli elementi seguenti: `coclass`, `progid`o `vi_progid`.|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi COM](com-attributes.md)<br/>
[implements_category](implements-category.md)
