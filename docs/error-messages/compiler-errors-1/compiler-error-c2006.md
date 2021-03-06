---
title: Errore del compilatore C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 64f81929916cd3a4adf38a302ea34d46d9a5c070
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756552"
---
# <a name="compiler-error-c2006"></a>Errore del compilatore C2006

' Directive ' ha previsto un nome file. trovato ' token '

Le direttive, ad esempio [#include](../../preprocessor/hash-include-directive-c-cpp.md) o [#import](../../preprocessor/hash-import-directive-cpp.md) richiedono un nome file. Per risolvere l'errore, verificare che il *token* sia un nome di file valido. Inoltre, inserire il nome del file tra virgolette doppie o parentesi angolari.

L'esempio seguente genera l'C2006:

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

Possibile soluzione:

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```
