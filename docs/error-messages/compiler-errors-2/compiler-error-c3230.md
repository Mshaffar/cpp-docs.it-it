---
title: Errore del compilatore C3230
ms.date: 11/04/2016
f1_keywords:
- C3230
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
ms.openlocfilehash: 69ea279ac5e11c03f366711484ba0c250fc50225
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743315"
---
# <a name="compiler-error-c3230"></a>Errore del compilatore C3230

'function': un argomento di tipo modello per template' non può contenere un parametro di tipo generico: 'param'

Le istanze dei modelli vengono create in fase di compilazione, ma quelle dei generics vengono create in fase di esecuzione. Non è quindi possibile generare codice generico che può chiamare il modello perché non è possibile creare un'istanza del modello in fase di esecuzione quando il tipo generico è noto.

L'esempio seguente genera l'errore C3230:

```cpp
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```
