---
title: Mapping di messaggi Windows a classi
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 0f1207faca56acd709db86478722eba85eeb284a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685610"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mapping di messaggi Windows a classi

Se è necessaria la finestra di dialogo per gestire i messaggi di Windows, eseguire l'override delle funzioni del gestore appropriate. A tale scopo, scegliere la scheda **Visualizzazione classi** **Esplora soluzioni**, fare clic con il pulsante destro del mouse sulla classe che rappresenta la finestra di dialogo e scegliere [creazione guidata classe](reference/mfc-class-wizard.md). Utilizzare la procedura guidata per eseguire il [mapping dei messaggi](../mfc/reference/mapping-messages-to-functions.md) alla classe della finestra di dialogo. In questo modo viene scritta una voce della mappa messaggi per ogni messaggio e vengono aggiunte le funzioni membro del gestore di messaggi alla classe. Utilizzare l'editor di codice per scrivere codice nei gestori di messaggi.

È anche possibile eseguire l'override delle funzioni membro di [CDialog](../mfc/reference/cdialog-class.md) e delle relative classi di base, in particolare [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Che cosa si vuole sapere

- [Gestione e mapping dei messaggi](../mfc/message-handling-and-mapping.md)

- [Funzioni membro comunemente sottoposte a override](../mfc/commonly-overridden-member-functions.md)

- [Funzioni membro comunemente aggiunte](../mfc/commonly-added-member-functions.md)

## <a name="see-also"></a>Vedere anche

[Finestre di dialogo](../mfc/dialog-boxes.md)<br/>
[Utilizzo delle finestre di dialogo in MFC](../mfc/life-cycle-of-a-dialog-box.md)
