---
title: pointer_default (attributo COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.pointer_default
dev_langs:
- C++
helpviewer_keywords:
- pointer_default attribute
ms.assetid: 2d0c7bbc-a1e8-4337-9e54-e304523e2735
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e8ddf566082bfded1f20a2bfe04e7cef0b5dc14
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791109"
---
# <a name="pointerdefault"></a>pointer_default

Specifica l'attributo di puntatore predefinite per tutti i puntatori, ad eccezione dei puntatori di primo livello che vengono visualizzati nell'elenco di parametri.

## <a name="syntax"></a>Sintassi

```cpp
[ pointer_default(value) ]
```

### <a name="parameters"></a>Parametri

*valore*<br/>
Un valore che descrive il tipo di puntatore: **ptr**, **ref**, o **univoco**.

## <a name="remarks"></a>Note

Il **pointer_default** attributi di C++ ha la stessa funzionalità come la [pointer_default](/windows/desktop/Midl/pointer-default) attributo MIDL.

## <a name="example"></a>Esempio

Vedere l'esempio relativo [defaultvalue](defaultvalue.md) per un esempio dell'uso dei **pointer_default**.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**interface**|
|**Ripetibile**|No|
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi di interfaccia](interface-attributes.md)  