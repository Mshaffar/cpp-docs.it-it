---
title: Pragma pointers_to_members
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: 6058e3e4855eb745a01410e31eb9f454ef131ab1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821408"
---
# <a name="pointers_to_members-pragma"></a>Pragma pointers_to_members

**C++Specifico**

Specifica se un puntatore a un membro di classe può essere dichiarato prima della definizione di classe associata. Utilizzato per controllare le dimensioni del puntatore e il codice necessario per interpretare il puntatore.

## <a name="syntax"></a>Sintassi

> **#pragma pointers_to_members (** *pointer-Declaration* [ **,** *most-General-rappresentazione* ])

## <a name="remarks"></a>Note

È possibile inserire un pragma **pointers_to_members** nel file di origine come alternativa a usare le opzioni del compilatore [/VMB o/VMG](../build/reference/vmb-vmg-representation-method.md) o le [parole chiave di ereditarietà](../cpp/inheritance-keywords.md).

L'argomento *pointer-Declaration* specifica se è stato dichiarato un puntatore a un membro prima o dopo la definizione della funzione associata. L'argomento *pointer-Declaration* è uno dei due simboli seguenti:

| Argomento | Comments |
|--------------|--------------|
| **full_generality** | Genera codice sicuro e talvolta non ottimale. Usare **full_generality** se un puntatore a un membro viene dichiarato prima della definizione di classe associata. Questo argomento usa sempre la rappresentazione del puntatore specificata dall'argomento relativo alla *rappresentazione più generale* . Equivalente a/vmg. |
| **best_case** | Genera codice sicuro e ottimale mediante la rappresentazione basata sul caso migliore (best-case) per tutti i puntatori ai membri. Richiede di definire una classe prima di dichiarare un puntatore a un membro di tale classe. Il valore predefinito è **best_case**. |

L'argomento relativo alla *rappresentazione più generale* specifica la più piccola rappresentazione del puntatore che il compilatore può usare in modo sicuro per fare riferimento a qualsiasi puntatore a un membro di una classe in un'unità di conversione. L'argomento può essere uno dei valori seguenti:

| Argomento | Comments |
|--------------|--------------|
| **single_inheritance** | La rappresentazione più generale è un puntatore a una funzione membro a ereditarietà singola. Genera un errore se il modello di ereditarietà di una definizione di classe per cui viene dichiarato un puntatore a un membro è multiplo o virtuale. |
| **multiple_inheritance** | La rappresentazione più generale è un puntatore a una funzione membro a ereditarietà multipla. Genera un errore se il modello di ereditarietà di una definizione di classe per cui viene dichiarato un puntatore a un membro è virtuale. |
| **virtual_inheritance** | La rappresentazione più generale è un puntatore a una funzione membro a ereditarietà virtuale. Non genera mai un errore. **virtual_inheritance** è l'argomento predefinito quando viene utilizzato `#pragma pointers_to_members(full_generality)`. |

> [!CAUTION]
> Si consiglia di inserire il **pointers_to_members** pragma solo nel file di codice sorgente che si desidera influire e solo dopo le direttive di `#include`. Questa pratica riduce il rischio che il pragma influirà sugli altri file e che vengano accidentalmente specificate più definizioni per la stessa variabile, funzione o nome di classe.

## <a name="example"></a>Esempio

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**Specifico C++ finale**

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
