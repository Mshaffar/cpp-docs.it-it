---
title: 'Procedura: Informazioni sui comandi visualizzato nella barra di stato'
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: c93787b3799306d6008299e7c1be6e429bc4c2d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160289"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Procedura: Informazioni sui comandi visualizzato nella barra di stato

Quando si esegue la procedura guidata dell'applicazione per creare la struttura dell'applicazione, è possibile supportare una barra degli strumenti e una barra di stato. Solo un'opzione della procedura guidata dell'applicazione supporta entrambi. Quando è presente una barra di stato, l'applicazione fornisce automaticamente commenti e suggerimenti utili quando l'utente sposta il puntatore del mouse sugli elementi dei menu. L'applicazione visualizza automaticamente una stringa di richiesta nella barra di stato quando la voce di menu viene evidenziata. Ad esempio, quando l'utente sposta il puntatore del mouse **tagliare** comando il **modifica** menu, la barra di stato potrebbe visualizzare "Taglia la selezione e la inserisce negli Appunti" nell'area dei messaggi della barra di stato. Il prompt dei comandi consente all'utente di comprendere lo scopo della voce di menu. Ciò funziona anche quando l'utente fa clic su un pulsante della barra degli strumenti.

È possibile aggiungere a questa Guida in linea della barra di stato mediante la definizione di stringhe di richiesta per voci di menu che aggiungono al programma. A questo scopo, fornire le stringhe di richiesta quando si modificano le proprietà della voce di menu nell'editor dei menu. Le stringhe che è definire vengono archiviate nel file di risorse dell'applicazione. hanno gli stessi ID dei comandi in cui viene spiegato.

Per impostazione predefinita, la creazione guidata applicazione aggiunge **AFX_IDS_IDLEMESSAGE**, l'ID per un messaggio di "Ready" standard, che viene visualizzato quando il programma è in attesa di nuovi messaggi. Se si specifica l'opzione della Guida sensibile al contesto della procedura guidata dell'applicazione, il messaggio viene modificato in "Per altre informazioni, premere F1."

## <a name="see-also"></a>Vedere anche

[Gestione e mapping dei messaggi](../mfc/message-handling-and-mapping.md)
