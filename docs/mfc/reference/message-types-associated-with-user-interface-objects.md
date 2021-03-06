---
title: Tipi di messaggi associati a oggetti dell'interfaccia utente
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.uiobject.msgs
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
ms.openlocfilehash: 37638d12c65986d40e7df9f0fbfdef4b8207e418
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741579"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Tipi di messaggi associati a oggetti dell'interfaccia utente

Nella tabella seguente illustra i tipi di oggetti con cui si usa e i tipi di messaggi associati ad essi.

### <a name="user-interface-objects-and-associated-messages"></a>Oggetti dell'interfaccia utente e i messaggi associati

|ID oggetto|Messages|
|---------------|--------------|
|Nome della classe, che rappresenta la finestra che lo contiene|Messaggi di Windows appropriati a un [CWnd](../../mfc/reference/cwnd-class.md)-classe derivata: una finestra di dialogo, finestra, finestra figlio, finestra figlio MDI o finestra cornice di primo livello.|
|Identificatore del menu di scelta o tasto di scelta rapida|-Messaggio di comando (viene eseguita la funzione di programma).<br />-Messaggio UPDATE_COMMAND_UI (aggiorna dinamicamente la voce di menu).|
|Identificatore del controllo|Controllare i messaggi di notifica per il tipo di controllo selezionato.|

## <a name="see-also"></a>Vedere anche

[Mapping di messaggi a funzioni](../../mfc/reference/mapping-messages-to-functions.md)<br/>
[Aggiunta di funzionalità con creazioni guidate codice](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Aggiunta di una classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Aggiunta di una funzione membro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Aggiunta di una variabile membro](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Override di una funzione virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestore messaggi MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Esplorazione della struttura delle classi](../../ide/navigate-code-cpp.md)
