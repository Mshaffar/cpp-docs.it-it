---
title: "L'impostazione della modalità di un oggetto CStatusBarCtrl | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CStatusBarCtrl
dev_langs: C++
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 35f48a87a0b9526ad6150a700190f4509e1128d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>Impostazione della modalità di un oggetto CStatusBarCtrl
Sono disponibili due modalità per un `CStatusBarCtrl` oggetto: semplice e non semplice. Nella maggior parte dei casi, il controllo barra di stato avrà una o più parti, insieme a testo e probabilmente un'icona o icone. Si tratta della modalità semplice. Per ulteriori informazioni su questa modalità, vedere [inizializzazione delle parti di un oggetto CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).  
  
 Tuttavia, vi sono casi in cui è necessario solo per visualizzare una singola riga di testo. In questo caso, la modalità semplice è sufficiente per le proprie esigenze. Per modificare la modalità del `CStatusBarCtrl` oggetto su simple, effettuare una chiamata al [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple) funzione membro. Quando il controllo barra di stato è in modalità semplice, impostare il testo chiamando il **SetText** funzione membro, passando 255 come valore per il **nPane** parametro.  
  
 È possibile utilizzare il [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple) funzione per determinare la modalità di `CStatusBarCtrl` oggetto si trova in.  
  
> [!NOTE]
>  Se l'oggetto barra di stato viene modificato da non semplice su simple, o viceversa, la finestra viene immediatamente ridisegnata e, se applicabile, parti eventualmente definite vengono automaticamente ripristinati.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controlli](../mfc/controls-mfc.md)
