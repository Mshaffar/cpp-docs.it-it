---
title: Errore del compilatore C3493
ms.date: 11/04/2016
f1_keywords:
- C3493
helpviewer_keywords:
- C3493
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
ms.openlocfilehash: 178d1221886dc62edd9785d211e2189fa50962f4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738297"
---
# <a name="compiler-error-c3493"></a>Errore del compilatore C3493

impossibile acquisire in modo implicito 'var' perché non è stata specificata alcuna modalità di acquisizione predefinita

L'acquisizione di espressioni lambda vuota, `[]`, specifica che l'espressione lambda non acquisisce le variabili in modo esplicito o implicito.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Specificare una modalità di acquisizione predefinita oppure

- Acquisire una o più variabili in modo esplicito.

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore C3493 perché modifica una variabile esterna ma specifica la clausola di acquisizione vuota:

```cpp
// C3493a.cpp

int main()
{
   int m = 55;
   [](int n) { m = n; }(99); // C3493
}
```

## <a name="example"></a>Esempio

L'esempio seguente risolve l'errore C3493 specificando la modalità di acquisizione predefinita mediante riferimento.

```cpp
// C3493b.cpp

int main()
{
   int m = 55;
   [&](int n) { m = n; }(99);
}
```

## <a name="see-also"></a>Vedere anche

[Espressioni lambda](../../cpp/lambda-expressions-in-cpp.md)
