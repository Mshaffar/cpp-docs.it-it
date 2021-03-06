---
title: Pragma const_seg
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: 845583889eb922ba97d145eefe6bca280a83817b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220437"
---
# <a name="const_seg-pragma"></a>Pragma const_seg

Specifica la sezione (segmento) in cui le variabili [const](../cpp/const-cpp.md) vengono archiviate nel file oggetto (. obj).

## <a name="syntax"></a>Sintassi

> **#pragma const_seg (** ["*Section-name*" [ **,** "*section-class*"]] **)** \
> **#pragma const_seg (** { **push** | **pop** } [ **,** *Identifier* ] [ **,** "*Section-name*" [ **,** "*section-class*"]] **)**

### <a name="parameters"></a>Parametri

**spingere**\
Opzionale Inserisce un record nello stack interno del compilatore. Un **push** può avere un *identificatore* e un *nome di sezione*.

**popup**\
Opzionale Rimuove un record dall'inizio dello stack interno del compilatore. Un **pop** può avere un *identificatore* e un *nome di sezione*. È possibile estrarre più record usando un solo comando **pop** usando l' *identificatore*. Il *nome di sezione diventa il* nome della sezione const attiva dopo il pop.

*identificatore*\
Opzionale Se usato con **push**, assegna un nome al record nello stack interno del compilatore. Se utilizzato con **pop**, la direttiva estrae i record dallo stack interno finché non viene rimosso l' *identificatore* . Se l' *identificatore* non viene trovato nello stack interno, non viene estratto alcun elemento.

"*nome-sezione*" \
Opzionale Nome di una sezione. Quando viene utilizzato con **pop**, lo stack viene estratto e *Section-name* diventa il nome della sezione const attiva.

"*section-class*" \
Opzionale Ignorato, ma incluso per la compatibilità con le versioni C++ di Microsoft precedenti alla versione 2,0.

## <a name="remarks"></a>Note

Una *sezione* in un file oggetto è un blocco denominato di dati che viene caricato in memoria come unità. Una *sezione const* è una sezione che contiene dati costanti. In questo articolo i termini *Segment* e *Section* hanno lo stesso significato.

La direttiva **const_seg** pragma indica al compilatore di inserire tutti gli elementi di dati costanti dall'unità di conversione in una sezione const denominata *Section-name*. La sezione predefinita nel file oggetto per le variabili **const** è `.rdata`. Alcune variabili **const** , ad esempio i valori scalari, vengono automaticamente inline nel flusso di codice. Il codice inline non viene visualizzato `.rdata`in. Una direttiva pragma **const_seg** senza un parametro *Section-name* Reimposta il nome della sezione per gli elementi di dati **const** successivi su `.rdata`.

Se si definisce un oggetto che richiede l'inizializzazione dinamica `const_seg`in un, il risultato è un comportamento non definito.

Per un elenco di nomi che non devono essere usati per creare una sezione, vedere [/Section](../build/reference/section-specify-section-attributes.md).

È inoltre possibile specificare le sezioni per i dati inizializzati ([data_seg](../preprocessor/data-seg.md)), i dati non inizializzati ([bss_seg](../preprocessor/bss-seg.md)) e le funzioni ([code_seg](../preprocessor/code-seg.md)).

È possibile utilizzare [dumpbin. Applicazione EXE](../build/reference/dumpbin-command-line.md) per la visualizzazione dei file oggetto. Le versioni di DUMPBIN per ogni architettura di destinazione supportata sono incluse in Visual Studio.

## <a name="example"></a>Esempio

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
