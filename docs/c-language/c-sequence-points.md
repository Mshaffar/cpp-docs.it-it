---
title: Punti di sequenza C
ms.date: 11/04/2016
helpviewer_keywords:
- sequence points
ms.assetid: c84885a5-4336-4eba-a643-058df4249903
ms.openlocfilehash: 13d6044269f60dc426a8b0b9b03463f387dfaa10
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313337"
---
# <a name="c-sequence-points"></a>Punti di sequenza C

Il valore di un oggetto può essere modificato una sola volta da un'espressione tra "punti di sequenza" consecutivi. Il linguaggio C definisce i seguenti punti di sequenza:

- Operando sinistro dell'operatore AND logico (**&&**). L'operando sinistro dell'operatore logico AND viene valutato completamente e tutti gli effetti collaterali vengono completati prima di continuare. Se il secondo operando risulta essere false (0), l'altro operando non viene valutato.

- L'operando sinistro dell'operatore logico OR (`||`). L'operando sinistro dell'operatore logico OR viene valutato completamente e tutti gli effetti collaterali vengono completati prima di continuare. Se il secondo operando risulta essere true (diverso da zero), l'altro operando non viene valutato.

- L'operando sinistro dell'operatore virgola. L'operando sinistro dell'operatore virgola viene valutato completamente e tutti gli effetti collaterali vengono completati prima di continuare. Entrambi gli operandi dell'operatore virgola vengono sempre valutati. Si noti che l'operatore virgola in una chiamata di funzione non garantisce un ordine di valutazione.

- Operatore chiamata di funzione. Tutti gli argomenti a una funzione vengono valutati e tutti gli effetti collaterali vengono completati prima dell'accesso alla funzione. Nessun ordine di valutazione tra gli argomenti è specificato.

- Primo operando dell'operatore condizionale. Il primo operando dell'operatore condizionale viene valutato completamente e tutti gli effetti collaterali vengono completati prima di continuare.

- La fine di un'espressione di inizializzazione completa ovvero un'espressione che non fa parte di un'altra espressione come, ad esempio, la fine di un'inizializzazione in un'istruzione di dichiarazione).

- Espressione in un'istruzione di espressione. Le istruzioni di espressione sono costituite da un'espressione facoltativa seguita da un punto e virgola (**;**). L'espressione viene valutata per i relativi effetti collaterali ed esiste un punto di sequenza che segue questa valutazione.

- L'espressione di controllo in un'istruzione di selezione (**if** o `switch`). L'espressione viene valutata completamente e tutti gli effetti collaterali vengono completati prima che venga eseguito il codice dipendente dalla selezione.

- L'espressione di controllo di un'istruzione `while` o **do**. L'espressione viene valutata completamente e tutti gli effetti collaterali vengono completati prima che vengano eseguite eventuali istruzioni presenti nell'iterazione successiva del ciclo `while` o **do**.

- Ognuna delle tre espressioni di un'istruzione **for** . Le espressioni vengono valutate completamente e tutti gli effetti collaterali vengono completati prima dell'esecuzione di eventuali istruzioni presenti nell'iterazione successiva del ciclo **for**.

- L'espressione in un'istruzione `return`. L'espressione viene valutata completamente e tutti gli effetti collaterali vengono completati prima che il controllo torni alla funzione chiamante.

## <a name="see-also"></a>Vedere anche

[Valutazione delle espressioni](../c-language/expression-evaluation-c.md)
