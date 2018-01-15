---
title: Chiamata di codice dal Framework | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83eeb1c7fd3032ae33c213f17522b171bdb46e55
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="how-the-framework-calls-your-code"></a>Chiamate del codice dal framework
È fondamentale comprendere la relazione tra il codice sorgente e il codice nel framework MFC. Quando l'applicazione è in esecuzione, la maggior parte del flusso di controllo risiede nel codice del framework. Il framework gestisce il ciclo dei messaggi che riceve i messaggi da Windows mentre l'utente sceglie i comandi e modifica i dati in una visualizzazione. Gli eventi che possono essere gestiti autonomamente dal framework non si basano affatto sul codice sorgente. Ad esempio, il framework è in grado di chiudere le finestre e di uscire da un'applicazione in risposta ai comandi dell'utente. Dal momento che gestisce tali attività, il framework utilizza gestori di messaggi e funzioni virtuali C++ per fornire le possibilità di rispondere a questi eventi. Comunque il codice non è contenuto nel controllo; il framework lo è.  
  
 Il framework chiama il codice per eventi specifici dell'applicazione. Ad esempio, quando l'utente sceglie un comando del menu, il framework guida il comando lungo una sequenza di oggetti C++: la visualizzazione corrente e la finestra cornice, il documento associato alla visualizzazione, il modello di documento del documento e l'oggetto dell'applicazione. Se uno di questi oggetti può gestire il comando lo fa chiamando la funzione del gestore dei messaggi appropriata. Per qualsiasi comando specificato, il codice chiamato potrebbe essere quello del programmatore oppure quello del framework.  
  
 Questo comportamento è piuttosto familiare ai programmatori che hanno avuto esperienza con la programmazione tradizionale di Windows o con la programmazione basata su eventi.  
  
 Negli argomenti correlati, verranno illustrate le operazioni eseguite dal framework, quali l'inizializzazione e l'esecuzione dell'applicazione e la pulizia al termine dell'applicazione. Inoltre si comprenderà dove viene inserito il codice che si scrive.  
  
 Per ulteriori informazioni, vedere [classe CWinApp: classe Application](../mfc/cwinapp-the-application-class.md) e [modelli di documento e il processo di creazione documento/visualizzazione](../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione nel framework](../mfc/building-on-the-framework.md)
