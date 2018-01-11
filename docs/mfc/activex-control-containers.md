---
title: Contenitori di controlli ActiveX | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e564ee0c9d8ec47db68c49db1dfcbdc86b393e02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="activex-control-containers"></a>Contenitori di controlli ActiveX
Un contenitore di controlli ActiveX è un contenitore che supporta in modo completo i controlli ActiveX e può includerli nelle proprie finestre e finestre di dialogo. Un controllo ActiveX rappresenta un elemento di software riutilizzabile che è possibile utilizzare in molti progetti di sviluppo. I controlli consentono all'utente dell'applicazione di accedere ai database, di monitorare i dati e di effettuare varie selezioni all'interno delle applicazioni. Per ulteriori informazioni sui controlli ActiveX, vedere l'articolo [controlli ActiveX MFC](../mfc/mfc-activex-controls.md).  
  
 In genere i contenitori dei controlli possono assumere due forme in un progetto:  
  
-   Finestre di dialogo e finestre simili alle finestre di dialogo come le visualizzazioni di form, dove un controllo ActiveX viene utilizzato in qualche punto nella finestra di dialogo.  
  
-   Finestre in un'applicazione, dove un controllo ActiveX viene utilizzato in una barra degli strumenti o in un'altra posizione nella finestra dell'utente.  
  
 ActiveX contenitore del controllo interagisce con il controllo tramite esposti [metodi](../mfc/mfc-activex-controls-methods.md) e [proprietà](../mfc/mfc-activex-controls-properties.md). A questi metodi e proprietà, accessibili e modificabili dal contenitore dei controlli, è possibile accedere tramite una classe wrapper nel progetto del contenitore dei controlli ActiveX. Il controllo ActiveX incorporato può anche interagire con il contenitore generando (inviando) [eventi](../mfc/mfc-activex-controls-events.md) per notificare al contenitore che si è verificata un'azione. Il contenitore dei controlli può scegliere di agire o meno in seguito a queste notifiche.  
  
 Articoli aggiuntivi in cui vengono illustrati diversi argomenti, dalla creazione di un progetto del contenitore dei controlli ActiveX ai problemi di implementazione di base relativi ai contenitori dei controlli ActiveX creati con Visual C++:  
  
-   [Creazione di un contenitore di controlli ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [Contenitori per i controlli ActiveX](../mfc/containers-for-activex-controls.md)  
  
-   [Contenitori di controlli ActiveX: attivazione manuale del contenimento dei controlli ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [Contenitori di controlli ActiveX: inserimento di un controllo in un'applicazione contenitore di controlli](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [Contenitori di controlli ActiveX: connessione di un controllo ActiveX a una variabile membro](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [Contenitori di controlli ActiveX: Gestione di eventi da un ActiveX di controllo](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [Contenitori di controlli ActiveX: visualizzazione e modifica delle proprietà dei controlli](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [Contenitori di controlli ActiveX: programmazione di controlli ActiveX in un contenitore di controlli ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [Contenitori di controlli ActiveX: uso di controlli in un contenitore diverso da una finestra di dialogo](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 Per ulteriori informazioni sull'utilizzo dei controlli ActiveX in una finestra di dialogo, vedere il [finestra di dialogo Editor](../windows/dialog-editor.md) argomenti.  
  
 Per un elenco di articoli che descrivono i dettagli dello sviluppo di controlli ActiveX in Visual C++ e le classi di controlli ActiveX MFC, vedere [controlli ActiveX MFC](../mfc/mfc-activex-controls.md). Gli articoli sono raggruppati per categorie funzionali.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli ActiveX MFC](../mfc/mfc-activex-controls.md)
