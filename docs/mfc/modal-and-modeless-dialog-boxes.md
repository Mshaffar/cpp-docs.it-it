---
title: Finestre di dialogo modali e non modali | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 450a7576556cb1ecec394339c1e2d63264c5340b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="modal-and-modeless-dialog-boxes"></a>Finestre di dialogo modali e non modali
È possibile utilizzare una classe [CDialog](../mfc/reference/cdialog-class.md) per gestire due tipi di finestre di dialogo:  
  
-   *Finestre di dialogo modale*, che richiede all'utente di rispondere prima di continuare il programma  
  
-   *Finestre di dialogo non modale*, che rimangono sullo schermo e sono disponibili per l'utilizzo in qualsiasi momento, ma consentire attività utente  
  
 La modifica delle risorse e le procedure per la creazione di un modello di finestra di dialogo sono gli stessi per le finestre di dialogo modali e non.  
  
 La creazione di una finestra di dialogo per il programma richiede i passaggi seguenti:  
  
1.  Utilizzare il [editor finestre](../windows/dialog-editor.md) per progettare la finestra di dialogo e creare la risorsa modello di finestra di dialogo.  
  
2.  Creare una classe di finestra di dialogo.  
  
3.  Connettere il [controlli della risorsa finestra di dialogo per i gestori di messaggi](../windows/adding-event-handlers-for-dialog-box-controls.md) nella classe di finestra di dialogo.  
  
4.  Aggiungere i membri dati associati a controlli della finestra di dialogo e per specificare [DDX](../mfc/dialog-data-exchange.md) e [la convalida dei dati di finestra di dialogo](../mfc/dialog-data-validation.md) per i controlli.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre di dialogo](../mfc/dialog-boxes.md)   
 [Ciclo di vita di una finestra di dialogo](../mfc/life-cycle-of-a-dialog-box.md)
