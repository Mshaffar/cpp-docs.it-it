---
title: RDX (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f0140b759b1d78eb1284213a0dc47d9600b2a83b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214630"
---
# <a name="rdx"></a>rdx

Crea una chiave del registro di sistema o modifica una chiave del registro di sistema esistente.

## <a name="syntax"></a>Sintassi

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Parametri

*key*<br/>
Nome della chiave da creare o aprire.

*valueName*<br/>
Opzionale Specifica il campo del valore da impostare. Se un campo valore con questo nome non esiste già nella chiave, viene aggiunto.

*regtype*<br/>
Tipo di chiave del registro di sistema da aggiungere. Può essere uno dei seguenti: `text`, `dword`, `binary`o `CString`.

## <a name="remarks"></a>Osservazioni

L'attributo **RDX** C++ crea o modifica una chiave del registro di sistema esistente per un componente com. L'attributo aggiunge una BEGIN_RDX_MAP macro all'oggetto che implementa il membro di destinazione. `RegistryDataExchange`, una funzione inserita come risultato della macro BEGIN_RDX_MAP, può essere utilizzata per trasferire i dati tra il registro di sistema e i membri dati

Questo attributo può essere usato in combinazione con gli attributi [coclass](coclass.md), [ProgID](progid.md)o [vi_progid](vi-progid.md) o altri attributi che ne implicano uno di questi.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe** o membro **struct**|
|**Ripetibile**|No|
|**Attributi obbligatori**|nessuno|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Esempio

Il codice seguente aggiunge una chiave del registro di sistema denominata SetValue al sistema che descrive il componente COM CMyClass.

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>Vedere anche

[Attributi COM](com-attributes.md)<br/>
[registration_script](registration-script.md)
