---
title: Avviso del compilatore (livello 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: 54baf35eaeb5ef2c8add024f25c059480d60617b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186565"
---
# <a name="compiler-warning-level-1-c4508"></a>Avviso del compilatore (livello 1) C4508

' Function ': la funzione deve restituire un valore. viene utilizzato il tipo restituito ' void '

Per la funzione non è stato specificato alcun tipo restituito. In questo caso, deve essere attivato anche C4430 e il compilatore implementa la correzione restituita da C4430 (il valore predefinito è int).

Per risolvere il problema, dichiarare in modo esplicito il tipo restituito di funzioni.

L'esempio seguente genera l'C4508:

```cpp
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```
