---
title: appobject (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.appobject
helpviewer_keywords:
- appobject attribute
ms.assetid: 8ce30b73-e945-403e-a755-6bc78078a695
ms.openlocfilehash: ebbb3ce71dc9b947ef49a42ee41a5ce2d5abbb34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168512"
---
# <a name="appobject"></a>appobject

Identifica la coclasse come oggetto applicazione, che è associato a un'applicazione exe completa, e indica che le funzioni e le proprietà della coclasse sono disponibili a livello globale in questa [libreria dei tipi](../../mfc/automation-clients-using-type-libraries.md).

## <a name="syntax"></a>Sintassi

```cpp
[appobject]
```

## <a name="remarks"></a>Osservazioni

L'attributo **appobject** C++ ha la stessa funzionalità dell'attributo MIDL di [appobject](/windows/win32/Midl/appobject) .

## <a name="example"></a>Esempio

Il codice seguente illustra una semplice definizione di classe preceduta da un blocco di attributi che include **appobject**:

```cpp
// cpp_attr_ref_appobject.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib", uuid="f1ce17f0-a5df-4d26-95f6-0a122197ac5b")];

[object, uuid="905de6db-7a12-45ab-9f8b-b39f5112f010"]
__interface ICustom {};

[coclass, appobject,uuid="00395340-745f-4b69-bd58-e2921452b9fc"]
class A : public ICustom {
   int i;
};
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**|
|**Ripetibile**|No|
|**Attributi obbligatori**|`coclass`|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi di classe](class-attributes.md)<br/>
[Attributi Typedef, Enum, Union e Struct](typedef-enum-union-and-struct-attributes.md)
