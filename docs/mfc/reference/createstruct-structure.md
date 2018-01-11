---
title: Struttura CREATESTRUCT | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CREATESTRUCT
dev_langs: C++
helpviewer_keywords: CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 97ca66036930963028681b6179ac7176b0350166
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="createstruct-structure"></a>Struttura CREATESTRUCT
Il `CREATESTRUCT` struttura definisce i parametri di inizializzazione passati alla routine della finestra di un'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
typedef struct tagCREATESTRUCT {  
    LPVOID lpCreateParams;  
    HANDLE hInstance;  
    HMENU hMenu;  
    HWND hwndParent;  
    int cy;  
    int cx;  
    int y;  
    int x;  
    LONG style;  
    LPCSTR lpszName;  
    LPCSTR lpszClass;  
    DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### <a name="parameters"></a>Parametri  
 `lpCreateParams`  
 Punta ai dati da utilizzare per creare una finestra.  
  
 `hInstance`  
 Identifica l'handle dell'istanza di modulo del modulo che contiene la nuova finestra.  
  
 `hMenu`  
 Identifica il menu da utilizzare per la nuova finestra. Se una finestra figlio, contiene l'ID intero.  
  
 `hwndParent`  
 Identifica la finestra proprietaria della nuova finestra. Questo membro è **NULL** se la finestra nuova finestra di primo livello.  
  
 `cy`  
 Specifica l'altezza della nuova finestra.  
  
 `cx`  
 Specifica la larghezza della nuova finestra.  
  
 `y`  
 Specifica la coordinata y dell'angolo superiore sinistro della nuova finestra. Le coordinate sono rispetto alla finestra padre se la nuova finestra è una finestra figlio. in caso contrario le coordinate sono relative all'origine schermata.  
  
 `x`  
 Specifica la coordinata x dell'angolo superiore sinistro della nuova finestra. Le coordinate sono rispetto alla finestra padre se la nuova finestra è una finestra figlio. in caso contrario le coordinate sono relative all'origine schermata.  
  
 `style`  
 Specifica la nuova finestra [stile](../../mfc/reference/styles-used-by-mfc.md).  
  
 `lpszName`  
 Punta a una stringa con terminazione null che specifica il nome della nuova finestra.  
  
 `lpszClass`  
 Punta a una stringa con terminazione null che specifica nome di classe della finestra Nuovo Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struttura; per ulteriori informazioni, vedi il Windows SDK).  
  
 `dwExStyle`  
 Specifica il [stile esteso](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) per la nuova finestra.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** winuser.h  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture, stili, callback e mappe messaggi](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)

