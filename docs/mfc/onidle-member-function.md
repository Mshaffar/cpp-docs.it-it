---
title: Funzione membro OnIdle | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OnIdle
dev_langs: C++
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d601ac8da59e4b980c4f1a5bd85bc1b347e8e11e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="onidle-member-function"></a>Funzione membro OnIdle
Durante non l'elaborazione di messaggi Windows, il framework chiama la [CWinApp](../mfc/reference/cwinapp-class.md) funzione membro [OnIdle](../mfc/reference/cwinapp-class.md#onidle) (descritta in riferimenti alla libreria MFC).  
  
 Eseguire l'override `OnIdle` per eseguire attività in background. La versione predefinita aggiorna lo stato degli oggetti dell'interfaccia utente, ad esempio i pulsanti della barra degli strumenti e ne esegue la pulizia degli oggetti temporanei creati dal framework durante le operazioni. Nella figura seguente viene illustrato come il ciclo di messaggi chiama `OnIdle` quando non sono presenti messaggi nella coda.  
  
 ![Processo del ciclo di messaggi](../mfc/media/vc387c1.gif "vc387c1")  
Ciclo del messaggio  
  
 Per ulteriori informazioni sulle operazioni del ciclo inattivo, vedere [elaborazione di cicli di inattività](../mfc/idle-loop-processing.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CWinApp: classe Application](../mfc/cwinapp-the-application-class.md)