---
title: idl_module (C++ attributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_module
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
ms.openlocfilehash: 6dd0a34d5d957838613bde2c9e05d5ef26a1f678
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168044"
---
# <a name="idl_module"></a>idl_module

Specifica un punto di ingresso in un file con estensione dll.

## <a name="syntax"></a>Sintassi

```cpp
[ idl_module (name=module_name, dllname=dll, uuid="uuid", helpstring="help text", helpstringcontext=helpcontextID, helpcontext=helpcontext, hidden, restricted) ]
function declaration
```

### <a name="parameters"></a>Parametri

*nome*<br/>
Nome definito dall'utente per il blocco di codice che verrà visualizzato nel file con estensione IDL.

*DllName*<br/>
Opzionale Il file con estensione dll che contiene l'esportazione.

*uuid*<br/>
Opzionale ID univoco.

*helpstring*<br/>
Opzionale Stringa di caratteri utilizzata per descrivere la libreria dei tipi.

*helpstringcontext*<br/>
Opzionale ID di un argomento della Guida in un file con estensione hlp o CHM.

*helpcontext*<br/>
Opzionale ID della Guida per questa libreria dei tipi.

*hidden*<br/>
Opzionale Parametro che impedisce la visualizzazione della libreria. Per altre informazioni, vedere l'attributo MIDL [hidden](/windows/win32/Midl/hidden) .

*restricted*<br/>
Opzionale I membri della libreria non possono essere chiamati in modo arbitrario. Per altre informazioni, vedere l'attributo MIDL [restricted](/windows/win32/Midl/restricted) .

*Dichiarazione di funzione*<br/>
Funzione che si vuole definire.

## <a name="remarks"></a>Osservazioni

L'attributo **idl_module** C++ consente di specificare il punto di ingresso in un file con estensione dll, che consente di importare da un file con estensione dll.

L'attributo **idl_module** dispone di funzionalità simili a quelle del [modulo](/windows/win32/Midl/module) MIDL Attribute.

È possibile esportare qualsiasi elemento da un oggetto COM che è possibile esportare da un file con estensione dll inserendo un punto di ingresso della DLL nel blocco di libreria di un file con estensione IDL.

Il deve usare **idl_module** in due passaggi. In primo luogo, è necessario definire una coppia nome/DLL. Quindi, quando si usa **idl_module** per specificare un punto di ingresso, specificare il nome e gli eventuali attributi aggiuntivi.

## <a name="example"></a>Esempio

Nel codice seguente viene illustrato come utilizzare l'attributo **idl_module** :

```cpp
// cpp_attr_ref_idl_module.cpp
// compile with: /LD
[idl_quote("midl_pragma warning(disable:2461)")];
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];
[idl_module(name="MyLib"), entry(4), usesgetlasterror]
void FuncName(int i);
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|Ovunque|
|**Ripetibile**|No|
|**Attributi obbligatori**|nessuno|
|**Attributi non validi**|nessuno|

Per altre informazioni, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi IDL](idl-attributes.md)<br/>
[Attributi autonomi](stand-alone-attributes.md)<br/>
[entry](entry.md)
