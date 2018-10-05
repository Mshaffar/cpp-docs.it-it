---
title: ProgID (attributo COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5e499a6faabda20450a7af76d97664b90464b36
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791140"
---
# <a name="progid"></a>progid

Specifica il ProgID di un oggetto COM.

## <a name="syntax"></a>Sintassi

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parametri

*name*<br/>
Il ProgID che rappresenta l'oggetto.

ProgID presentano una versione leggibile dell'identificatore di classe (CLSID) usato per identificare gli oggetti ActiveX/COM.

## <a name="remarks"></a>Note

Il **progid** attributo C++ consente di specificare il ProgID di un oggetto COM. Un ProgID ha il formato *name1.name2.version*. Se non si specifica un *versione* per un ProgID, la versione predefinita è 1. Se non si specifica *name1.name2*, il nome predefinito è *classname.classname*. Se non si specifica **progid** e si specifica `vi_progid`, *name1.name2* provengono da `vi_progid` e di (successivo numero sequenziale) versione viene aggiunto.

Se un blocco di attributi che utilizza **progid** non utilizza inoltre **uuid**, il compilatore verificherà il Registro di sistema per verificare se un **uuid** esiste per l'oggetto specificato **progid** . Se **progid** non viene specificato, la versione (e un nome (coclasse), se la creazione di una coclasse) verrà utilizzati per generare un **progid**.

**ProgID** implica la `coclass` dell'attributo, vale a dire, se si specifica **progid**, è la stessa operazione quello ottenuto specificando il `coclass` e **progid** attributi.

Il **progid** attributo fa sì che una classe da registrare automaticamente sotto il nome specificato. Il file con estensione IDL generato non verrà visualizzata la **progid** valore.

Quando questo attributo viene usato all'interno di un progetto che usa ATL, il comportamento dell'attributo cambia. Oltre al comportamento precedente, le informazioni specificate con questo attributo viene utilizzate nel `GetProgID` funzione, inserito dal `coclass` attributo. Per altre informazioni, vedere la [coclasse](coclass.md) attributo.

## <a name="example"></a>Esempio

Vedere l'esempio relativo [coclasse](coclass.md) per un esempio dell'uso dei **progid**.

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**|
|**Ripetibile**|No|
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi di classe](class-attributes.md)<br/>
[Attributi Typedef, Enum, Union e Struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Chiave progID](/windows/desktop/com/-progid--key)  