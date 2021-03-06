---
title: Errore del compilatore C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: 8c62117e9437233f614aa0e57a3848fcb8dd0c79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754849"
---
# <a name="compiler-error-c3854"></a>Errore del compilatore C3854

l'espressione a sinistra di ' =' restituisce una funzione. Non è possibile assegnare a una funzione (una funzione non è un l-value)

Non è possibile reinizializzare un riferimento. La dereferenziazione di un riferimento a una funzione produce una funzione, che è un rvalue, a cui non è possibile assegnare. Pertanto, non è possibile assegnare tramite un riferimento a una funzione.

L'esempio seguente genera l'C3854:

```cpp
// C3854.cpp
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);
typedef int (* pFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   pFunc_t pf = &afunc;   // OK initializing a pointer to function

   *pf = &afunc;   // C3854
   // try the following line instead
   // pf = &afunc;
   *rf = &afunc;   // C3854
}
```
