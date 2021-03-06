---
title: Istruzione return (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: c8ea796ab40a2090ed9853377f7c9415914bc0e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178982"
---
# <a name="return-statement-c"></a>Istruzione return (C++)

Viene interrotta l'esecuzione di una funzione e il controllo viene restituito alla funzione chiamante (o al sistema operativo, se il controllo viene trasferito dalla funzione `main`). Nella funzione chiamante, l'esecuzione riprende dal punto immediatamente successivo alla chiamata.

## <a name="syntax"></a>Sintassi

```
return [expression];
```

## <a name="remarks"></a>Osservazioni

La clausola `expression`, se presente, viene convertita nel tipo specificato nella dichiarazione di funzione, come se si eseguisse un'inizializzazione. La conversione dal tipo dell'espressione al tipo **restituito** della funzione può creare oggetti temporanei. Per ulteriori informazioni su come e quando vengono creati temporaries, vedere [oggetti temporanei](../cpp/temporary-objects.md).

Il valore della clausola `expression` viene restituito alla funzione chiamante. Se l'espressione viene omessa, il valore restituito della funzione è indefinito. I costruttori e i distruttori e le funzioni di tipo **void**non possono specificare un'espressione nell'istruzione **Return** . Le funzioni di tutti gli altri tipi devono specificare un'espressione nell'istruzione **return** .

Quando il flusso di controllo esce dal blocco che include la definizione della funzione, il risultato è lo stesso che sarebbe se fosse stata eseguita un'istruzione **return** senza un'espressione. Ciò non è valido per le funzioni che vengono dichiarate come elementi che restituiscono un valore.

Una funzione può avere un numero qualsiasi di istruzioni **return** .

Nell'esempio seguente viene utilizzata un'espressione con un'istruzione **return** per ottenere il più elevato tra due numeri interi.

## <a name="example"></a>Esempio

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>Vedere anche

[Istruzioni di spostamento](../cpp/jump-statements-cpp.md)<br/>
[Parole chiave](../cpp/keywords-cpp.md)
