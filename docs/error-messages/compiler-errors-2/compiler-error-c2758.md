---
title: Errore del compilatore C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c854aeff1c57b8be6b445bc3615008519ca00af7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759516"
---
# <a name="compiler-error-c2758"></a>Errore del compilatore C2758

'member': un membro di tipo di riferimento deve essere inizializzato

L'errore del compilatore C2758 si verifica quando il costruttore non inizializza un membro del tipo riferimento in un elenco di inizializzatori. Il compilatore lascia il membro non definito. È necessario che le variabili del membro di riferimento siano inizializzate quando vengono dichiarate o che ricevano un valore nell'elenco di inizializzazione del costruttore.

L'esempio seguente genera l'errore C2758:

```cpp
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```
