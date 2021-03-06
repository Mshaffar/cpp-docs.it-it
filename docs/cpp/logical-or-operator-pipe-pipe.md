---
title: 'Operatore OR logico: ||'
ms.date: 06/14/2018
f1_keywords:
- '||'
helpviewer_keywords:
- OR operator [C++], logical
- '|| operator'
- OR operator
- logical OR operator
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
ms.openlocfilehash: 94b2bc024dd7223ac7adacc72924f5ee289bab37
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178080"
---
# <a name="logical-or-operator-"></a>Operatore OR logico: ||

## <a name="syntax"></a>Sintassi

> Logical- *or-expression* **||** *Logical-and-Expression*

## <a name="remarks"></a>Osservazioni

L'operatore OR logico ( **||** ) restituisce il valore booleano true se uno o entrambi gli operandi sono true e restituisce false in caso contrario. Gli operandi vengono convertiti in modo implicito nel tipo **bool** prima della valutazione e il risultato è di tipo **bool**. L'operatore OR logico presenta un'associatività da sinistra a destra.

Gli operandi dell'operatore OR logico non devono essere dello stesso tipo, ma devono essere di tipo integrale o di tipo puntatore. Gli operandi sono in genere espressioni di uguaglianza o relazionali.

Il primo operando viene completamente restituito e tutti gli effetti collaterali vengono completati prima di continuare la restituzione dell'espressione OR logica.

Il secondo operando viene restituito solo se il primo operando restituisce false (0). In questo modo si evita la valutazione del secondo operando quando l'espressione OR logica è true.

```cpp
printf( "%d" , (x == w || x == y || x == z) );
```

Nell'esempio precedente, se `x` è uguale a `w`, `y` o a `z`, il secondo argomento della funzione `printf` restituisce true e il valore 1 viene stampato. In caso contrario, restituisce false e il valore 0 viene formattato. Appena una delle condizioni restituisce true, la restituzione viene interrotta.

## <a name="operator-keyword-for-124124"></a>Parola chiave operator per&#124;&#124;

L'operatore **or** è il testo equivalente di **||** . Esistono due modi per accedere all'operatore **or** nei programmi: includere il file di intestazione \<iso646. h > o compilare con l'opzione del compilatore [/za](../build/reference/za-ze-disable-language-extensions.md) (Disable Language Extensions).

## <a name="example"></a>Esempio

```cpp
// expre_Logical_OR_Operator.cpp
// compile with: /EHsc
// Demonstrate logical OR
#include <iostream>
using namespace std;
int main() {
   int a = 5, b = 10, c = 15;
   cout  << boolalpha
         << "The true expression "
         << "a < b || b > c yields "
         << (a < b || b > c) << endl
         << "The false expression "
         << "a > b || b > c yields "
         << (a > b || b > c) << endl;
}
```

## <a name="see-also"></a>Vedere anche

[C++Precedenza e associatività degli operatori predefiniti](cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatori predefiniti C++, precedenza e associazione](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operatori logici C](../c-language/c-logical-operators.md)
