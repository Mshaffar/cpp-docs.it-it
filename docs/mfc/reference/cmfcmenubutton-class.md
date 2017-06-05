---
title: Classe CMFCMenuButton | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuButton class
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
caps.latest.revision: 32
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 65c334ce68dbbbae2b21da2c40aa9420cdeb51bd
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmenubutton-class"></a>Classe CMFCMenuButton
Pulsante che consente di visualizzare un menu di scelta rapida e segnala le selezioni di menu dell'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCMenuButton : public CMFCButton  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Costruisce un oggetto `CMFCMenuButton`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Chiamato dal framework per convertire i messaggi della finestra prima che vengano inviati. Esegue l'override di `CMFCButton::PreTranslateMessage`.|  
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Modifica la dimensione del pulsante in base alle dimensioni di testo e immagine.|  
  
### <a name="data-members"></a>Membri di dati  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Specifica se visualizzare il menu a comparsa sistema predefinito o utilizzare [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).|  
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Specifica se il menu di scelta rapida verrà visualizzato di sotto o a destra del pulsante.|  
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Specifica se il pulsante di menu Modifica il proprio stato dopo che l'utente rilascia il pulsante.|  
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Handle per il menu di Windows associata.|  
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|L'utente ha un identificatore che indica quale elemento selezionato nel menu a comparsa.|  
  
## <a name="remarks"></a>Note  
 Il `CMFCMenuButton` viene derivata dal [CMFCButton classe](../../mfc/reference/cmfcbutton-class.md) che, a sua volta deriva dal [CButton classe](../../mfc/reference/cbutton-class.md). Pertanto, è possibile utilizzare `CMFCMenuButton` nel codice esattamente come si utilizzerebbe `CButton`.  
  
 Quando si crea un `CMFCMenuButton`, è necessario passare un handle al menu di scelta rapida associato. Quindi, chiamare la funzione `CMFCMenuButton::SizeToContent`. `CMFCMenuButton::SizeToContent`verifica che le dimensioni del pulsante siano sufficiente per includere una freccia che punta alla posizione in cui verrà visualizzata la finestra popup, vale a dire, di sotto o a destra del pulsante.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come impostare l'handle del menu associato al pulsante, ridimensionare il pulsante in base alle dimensioni di testo e immagine e impostare il menu a comparsa viene visualizzato dal framework. Questo frammento di codice fa parte di [esempio nuovi controlli](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls&#38;](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls&#39;](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
 [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxmenubutton.h  
  
##  <a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton  
 Costruisce un nuovo [CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md) oggetto.  
  
```  
CMFCMenuButton();
```  
  
##  <a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu  
 Una variabile membro di tipo Boolean che indica il menu di scelta rapida visualizzato dal framework.  
  
```  
BOOL m_bOSMenu;  
```  
  
### <a name="remarks"></a>Note  
 Se `m_bOSMenu` è `TRUE`, il framework chiama ereditato `TrackPopupMenu` metodo per questo oggetto. In caso contrario, il framework chiama [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu).  
  
##  <a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow  
 Una variabile membro di tipo Boolean che indica la posizione del menu a comparsa.  
  
```  
BOOL m_bRightArrow;  
```  
  
### <a name="remarks"></a>Note  
 Quando l'utente preme il tasto menu, l'applicazione viene visualizzato un menu a comparsa. Il framework verrà visualizzato il menu a comparsa sotto il pulsante o a destra del pulsante. Il pulsante offre inoltre una piccola freccia che indica dove verrà visualizzato il menu a comparsa. Se `m_bRightArrow` è `TRUE`, il framework consente di visualizzare il menu a comparsa a destra del pulsante. In caso contrario, viene visualizzato il menu a comparsa sotto il pulsante.  
  
##  <a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed  
 Una variabile membro di tipo Boolean che indica se il pulsante di menu viene premuto mentre l'utente effettua una selezione dal menu a comparsa.  
  
```  
BOOL m_bStayPressed;  
```  
  
### <a name="remarks"></a>Note  
 Se il `m_bStayPressed` membro è `FALSE`, non diventano premuto il pulsante di menu quando l'utilizza fa clic sul pulsante. In questo caso, il framework consente di visualizzare il menu di scelta rapida.  
  
 Se il `m_bStayPressed` membro è `TRUE`, diventa premuto il pulsante di menu quando l'utente fa clic sul pulsante. Rimane premuto fino a dopo che l'utente chiude il menu a comparsa, effettuare una selezione o l'annullamento.  
  
##  <a name="m_hmenu"></a>CMFCMenuButton::m_hMenu  
 Handle per il menu associato.  
  
```  
HMENU m_hMenu;  
```  
  
### <a name="remarks"></a>Note  
 Il framework Visualizza il menu indicato da questa variabile membro quando l'utente fa clic sul pulsante di menu.  
  
##  <a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult  
 Intero che indica quale elemento l'utente seleziona dal menu a comparsa.  
  
```  
int m_nMenuResult;  
```  
  
### <a name="remarks"></a>Note  
 Il valore di questa variabile membro è zero se l'utente annulla il menu senza effettuare una selezione o se si verifica un errore.  
  
##  <a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage  
 Chiamato dal framework per convertire i messaggi della finestra prima che vengano inviati.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `pMsg`  
 Punta a un [MSG](../../mfc/reference/msg-structure1.md) struttura che contiene il messaggio da elaborare.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se il messaggio è stato convertito e non deve essere inviato; 0 se il messaggio non è stato convertito e deve essere inviato.  
  
### <a name="remarks"></a>Note  
  
##  <a name="sizetocontent"></a>CMFCMenuButton::SizeToContent  
 Modifica la dimensione del pulsante in base alla relativa dimensione del testo e dell'immagine.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `bCalcOnly`  
 Un parametro booleano che indica se questo metodo deve essere ridimensionato il pulsante.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [CSize](../../atl-mfc-shared/reference/csize-class.md) oggetto che specifica la nuova dimensione per il pulsante.  
  
### <a name="remarks"></a>Note  
 Se si chiama questa funzione e `bCalcOnly` è `TRUE`, `SizeToContent` calcolerà la nuova dimensione del pulsante.  
  
 Le nuove dimensioni del pulsante viene calcolata per adattare il testo del pulsante, immagine e direzione. Il framework aggiunge anche i margini predefiniti di 10 pixel del bordo orizzontale e 5 pixel del bordo verticale.  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCButton](../../mfc/reference/cmfcbutton-class.md)
