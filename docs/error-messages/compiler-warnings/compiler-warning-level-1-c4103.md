---
title: Avviso del compilatore (livello 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: dfc3a91b2dcb3ed1e8f4f4993edd67219a6bf1d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163845"
---
# <a name="compiler-warning-level-1-c4103"></a>Avviso del compilatore (livello 1) C4103

' filename ': l'allineamento è stato modificato dopo l'inclusione dell'intestazione, probabilmente a causa della mancata #pragma pack (pop)

L'operazione di compressione influiscono sul layout delle classi e, in genere, in caso di compressione delle modifiche nei file di intestazione, possono verificarsi problemi.

Usare #pragma [Pack](../../preprocessor/pack.md)(pop) prima di uscire dal file di intestazione per risolvere l'avviso.

L'esempio seguente genera l'C4103:

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

E quindi,

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```
