---
title: Avviso del compilatore (livello 3) C4554
ms.date: 11/04/2016
f1_keywords:
- C4554
helpviewer_keywords:
- C4554
ms.assetid: 55bb68f0-2e80-4330-8921-51083c4f8d53
ms.openlocfilehash: 45f9d85f272bb5093fd418981ea3dbdc8cb7f1c0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992012"
---
# <a name="compiler-warning-level-3-c4554"></a>Avviso del compilatore (livello 3) C4554

' operator ': controllare la precedenza degli operatori per un errore possibile. usare le parentesi per chiarire la precedenza

L'esempio seguente genera l'C4554:

```cpp
// C4554.cpp
// compile with: /W3 /WX
int main() {
   int a = 0, b = 0, c = 0;
   a = a << b + c;   // C4554
   // probably intended (a << b) + c,
   // but will get a << (b + c)
}
```
