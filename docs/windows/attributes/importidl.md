---
title: importidl (attributo COM C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.importidl
dev_langs:
- C++
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d1c022a48ef5510f67355af3af1ff0a0e98ad4c4
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791309"
---
# <a name="importidl"></a>importidl

Inserisce il file con estensione idl specificato nel file con estensione IDL generato.

## <a name="syntax"></a>Sintassi

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>Parametri

*idl_file*<br/>
Identifica il nome del file con estensione idl che si desidera eseguire il merge con il file con estensione idl che verrà generato per l'applicazione.

## <a name="remarks"></a>Note

Il **importidl** attributo C++ inserisce la sezione all'esterno del blocco di libreria (in *idl_file*) nel file IDL generato del programma e la sezione della libreria (in *idl_file*) nella libreria sezione del programma generati file con estensione idl.

È possibile usare **importidl**, ad esempio, se si desidera utilizzare un file con estensione idl codificato manualmente con il file con estensione IDL generato.

## <a name="example"></a>Esempio

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|Ovunque|
|**Ripetibile**|No|
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|nessuno|

Per altre informazioni, vedere [contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi del compilatore](compiler-attributes.md)<br/>
[Attributi autonomi](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[include](include-cpp.md)<br/>
[includelib](includelib-cpp.md)  