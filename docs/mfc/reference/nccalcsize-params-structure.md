---
title: Struttura NCCALCSIZE_PARAMS | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 88c25fd5e5862d5f0954ae853442c66eaf7320c8
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="nccalcsizeparams-structure"></a>Struttura NCCALCSIZE_PARAMS
Il `NCCALCSIZE_PARAMS` struttura contiene informazioni che un'applicazione può utilizzare durante l'elaborazione di `WM_NCCALCSIZE` per calcolare la dimensione, posizione e contenuto valido dell'area client di una finestra di messaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>Parametri  
 *rgrc*  
 Specifica una matrice di rettangoli. Il primo contiene le nuove coordinate di una finestra che è stato spostato o ridimensionato. Il secondo contiene le coordinate della finestra prima che è stata spostata o ridimensionata. La terza contiene le coordinate dell'area client di una finestra prima che è stata spostata o ridimensionata. Se la finestra è una finestra figlio, le coordinate sono relative l'area client della finestra padre. Se la finestra è una finestra di primo livello, le coordinate sono relative allo schermo.  
  
 *lppos*  
 Punta a un [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) struttura che contiene i valori di dimensioni e la posizione specificati nell'operazione che ha causato la finestra per essere spostato o ridimensionato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** winuser.h  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture, stili, callback e mappe messaggi](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

