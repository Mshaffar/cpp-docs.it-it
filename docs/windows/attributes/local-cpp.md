---
title: local (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: d3710eee748a43a1daa5c07d8b3feb6beb8f64fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214747"
---
# <a name="local-c"></a>local (C++)

Quando viene usato nell'intestazione dell'interfaccia, consente di usare il compilatore MIDL come generatore di intestazioni. Se utilizzata in una singola funzione, definisce una procedura locale per la quale non vengono generati stub.

## <a name="syntax"></a>Sintassi

```cpp
[local]
```

## <a name="remarks"></a>Osservazioni

L'attributo **local** C++ ha la stessa funzionalità dell'attributo MIDL [locale](/windows/win32/Midl/local) .

## <a name="example"></a>Esempio

Per un esempio su come usare **local**, vedere [call_as](call-as.md) .

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**interfaccia**, metodo di interfaccia|
|**Ripetibile**|No|
|**Attributi obbligatori**|nessuno|
|**Attributi non validi**|`dispinterface`|

Per altre informazioni, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi di interfaccia](interface-attributes.md)<br/>
[Attributi di metodo](method-attributes.md)<br/>
[call_as](call-as.md)
