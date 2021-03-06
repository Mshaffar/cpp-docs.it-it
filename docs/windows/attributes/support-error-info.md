---
title: support_error_info (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: e61ef2efbdc4039f496d7ffbcccc37cc8d111935
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166146"
---
# <a name="support_error_info"></a>support_error_info

Implementa il supporto per la restituzione di errori dettagliati.

## <a name="syntax"></a>Sintassi

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>Parametri

*error_interface*<br/>
Identificatore dell'interfaccia che implementa `IErrorInfo`.

## <a name="remarks"></a>Osservazioni

L'attributo **support_error_info** di C++ implementa il supporto per la restituzione di errori contestuali e dettagliati rilevati dall'oggetto di destinazione al client. Perché l'oggetto supporti gli errori, i metodi dell'interfaccia `IErrorInfo` devono essere implementati dall'oggetto. Per altre informazioni, vedere [Supporto di IDispatch e IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md).

Questo attributo aggiunge la classe [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) come classe base per l'oggetto di destinazione. Ciò comporta un'implementazione predefinita di `ISupportErrorInfo` e può essere usato quando una singola interfaccia genera errori in un oggetto.

## <a name="example"></a>Esempio

Il codice seguente aggiunge il supporto predefinito per l'interfaccia `ISupportErrorInfo` all'oggetto `CMyClass`.

```cpp
// cpp_attr_ref_support_error_info.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="mymod")];
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]
__interface IMyErrors
{
};

[ coclass, support_error_info("IMyErrors"),
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]
class CMyClass
{
};
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**class**|
|**Ripetibile**|Sì|
|**Attributi obbligatori**|nessuno|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi COM](com-attributes.md)<br/>
[Attributi di classe](class-attributes.md)
