---
title: Avviso del compilatore C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
helpviewer_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: 00c3e01f46bc98baff1b266bb8ee445b0f868522
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165015"
---
# <a name="compiler-warning-level-4-c4868"></a>Avviso del compilatore (livello 4) C4868

> il compilatore '_file_(*Line_number*)' non può applicare l'ordine di valutazione da sinistra a destra nell'elenco di inizializzatori tra parentesi graffe

Gli elementi di un elenco di inizializzatori tra parentesi graffe devono essere valutati in ordine da sinistra a destra. Esistono due casi in cui il compilatore non è in grado di garantire questo ordine: il primo è quando alcuni degli elementi sono oggetti passati per valore. il secondo è quando si esegue la compilazione con `/clr` e alcuni elementi sono campi di oggetti o sono elementi di matrice. Quando il compilatore non può garantire la valutazione da sinistra a destra, emette un avviso C4868.

Questo avviso può essere generato come risultato delle operazioni di conformità del compilatore eseguite per Visual Studio 2015 Update 2. Il codice compilato prima di Visual Studio 2015 Update 2 ora può generare C4868.

Per impostazione predefinita, questo avviso non è attivo. Usare `/Wall` per attivare questo avviso.

Per risolvere il problema, considerare prima di tutto se è necessaria la valutazione da sinistra a destra degli elementi dell'elenco di inizializzatori, ad esempio quando la valutazione degli elementi potrebbe produrre effetti collaterali dipendenti dall'ordine. In molti casi, l'ordine in cui vengono valutati gli elementi non ha un effetto osservabile.

Se l'ordine di valutazione deve essere da sinistra a destra, valutare se è possibile passare gli elementi in base `const` riferimento. Una modifica, ad esempio, Elimina l'avviso nell'esempio di codice seguente.

## <a name="example"></a>Esempio

Questo esempio genera C4868 e Mostra come risolverlo:

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```
