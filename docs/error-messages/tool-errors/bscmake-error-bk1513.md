---
title: Errore BK1513 di BSCMAKE
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: 3a16163f33814be18a67833995362ee9b13d8118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197639"
---
# <a name="bscmake-error-bk1513"></a>Errore BK1513 di BSCMAKE

l'aggiornamento non incrementale richiede tutti i file SBR

Non è possibile usare BSCMAKE per generare un nuovo file di informazioni (BSC) di visualizzazione poiché uno o più file SBR sono troncati. Per trovare i nomi dei file SBR troncati, leggere gli avvisi [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) che accompagnano questo errore.

BSCMAKE consente di aggiornare un file BSC con un file SBR troncato ma non di compilarne uno nuovo. BSCMAKE potrebbe creare un nuovo file BSC per i seguenti motivi:

- File BSC mancante.

- Nome file errato specificato per il file BSC.

- File BSC danneggiato.

Per risolvere il problema, eliminare i file SBR troncati, ricostruire o pulire la soluzione, quindi ricompilare. Nell'IDE scegliere **Compila**, **Pulisci soluzione**, quindi scegliere **Compila**, **Ricompila soluzione**.
