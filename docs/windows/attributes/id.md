---
title: ID (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 79e49b2c074cd82323c74489e33812c10c442c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168057"
---
# <a name="id"></a>id

Specifica un parametro *DISPID* per una funzione membro, ovvero una proprietà o un metodo, in un'interfaccia o in un'interfaccia dispatch.

## <a name="syntax"></a>Sintassi

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>Parametri

*DISPID*<br/>
ID dispatch per il metodo di interfaccia.

## <a name="remarks"></a>Osservazioni

L'attributo **ID** C++ ha la stessa funzionalità dell'attributo MIDL dell' [ID](/windows/win32/Midl/id) .

## <a name="example"></a>Esempio

Per un esempio su come usare l' **ID**, vedere l'esempio relativo a [Bindable](bindable.md) .

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|Metodo di interfaccia|
|**Ripetibile**|No|
|**Attributi obbligatori**|nessuno|
|**Attributi non validi**|nessuno|

Per altre informazioni, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi di metodo](method-attributes.md)<br/>
[Attributi di membro dati](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)
