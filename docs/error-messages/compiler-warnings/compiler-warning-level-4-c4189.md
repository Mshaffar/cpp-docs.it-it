---
title: Avviso del compilatore (livello 4) C4189
ms.date: 11/04/2016
f1_keywords:
- C4189
helpviewer_keywords:
- C4189
ms.assetid: 7ad9242c-228e-4054-8244-5e914b618ef3
ms.openlocfilehash: d403373fe200f10cb2f2c210b8cd8f58b7429198
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991502"
---
# <a name="compiler-warning-level-4-c4189"></a>Avviso del compilatore (livello 4) C4189

'identifier': variabile locale inizializzata ma senza riferimenti

Una variabile è stata dichiarata e inizializzata, ma non usata.

L'esempio seguente genera l'errore C4189:

```cpp
// C4189.cpp
// compile with: /W4
int main() {
   int a = 1;   // C4189, remove declaration to resolve
}
```
