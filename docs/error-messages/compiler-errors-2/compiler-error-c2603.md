---
title: Errore del compilatore C2603
ms.date: 11/04/2016
f1_keywords:
- C2603
helpviewer_keywords:
- C2603
ms.assetid: 9ca520d0-f082-4b65-933d-17c3bcf8b02c
ms.openlocfilehash: e4540180058c890a1dec9c4060f796f1f044c934
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447989"
---
# <a name="compiler-error-c2603"></a>Errore del compilatore C2603

> «*funzione*': Troppi oggetti statici in ambito blocco con costruttore/o distruttori nella funzione

Nelle versioni di Microsoft C++ compilatore prima di Visual Studio 2015, o quando il [/Zc:threadSafeInit-](../../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) viene specificata l'opzione del compilatore, è previsto un limite pari a 31, sul numero di oggetti statici è possibile avere in visibile esternamente funzione inline.

Per risolvere questo problema, è consigliabile adottare la versione più recente di Microsoft C++ set di strumenti del compilatore, o, se possibile, rimuovere l'opzione del compilatore /Zc:threadSafeInit-. Se questo non è possibile, provare a usare gli oggetti statici. Se gli oggetti sono dello stesso tipo, provare a usare una singola matrice statica di quel tipo e fare riferimento a singoli membri in base alle esigenze.

## <a name="example"></a>Esempio

Il codice seguente genera l'errore C2603 e viene illustrato un modo per risolvere il problema:

```cpp
// C2603.cpp
// Compile by using: cl /W4 /c /Zc:threadSafeInit- C2603.cpp
struct C { C() {} };
extern inline void f1() {
    static C C01, C02, C03, C04, C05, C06, C07, C08, C09, C10;
    static C C11, C12, C13, C14, C15, C16, C17, C18, C19, C20;
    static C C21, C22, C23, C24, C25, C26, C27, C28, C29, C30, C31;
    static C C32;   // C2603 Comment this line out to avoid error
}
```
