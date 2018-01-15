---
title: Classe CMFCPropertyGridToolTipCtrl | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
dev_langs: C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9a0b4a43da8943bc196a799ca4419dea7f34ed76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Classe CMFCPropertyGridToolTipCtrl
Implementa una descrizione comando controllare che il [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md) viene utilizzata per visualizzare le descrizioni comandi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|||  
|-|-|  
|Nome|Descrizione|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Costruisce un oggetto `CMFCPropertyGridToolTipCtrl`.|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Distruttore.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|Nome|Descrizione|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crea una finestra per il controllo tooltip.|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Disattiva e nasconde il controllo tooltip.|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Restituisce le coordinate dell'ultima posizione del controllo tooltip.|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Nasconde il controllo tooltip.|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Usato dalla classe [CWinApp](../../mfc/reference/cwinapp-class.md) per convertire i messaggi della finestra prima che vengano inviati alle funzioni Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) e [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) . Esegue l'override di [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Imposta la spaziatura tra il testo della descrizione comando e il bordo della finestra della descrizione comando.|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Visualizza il controllo descrizione comando.|  
  
## <a name="remarks"></a>Note  
 Le descrizioni comandi quando il puntatore è posizionato su un nome di proprietà. Il [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) classe visualizza una descrizione comando in modo che sia facilmente leggibile dall'utente. In genere, la posizione di una descrizione comando è determinata dalla posizione del puntatore. Tramite questa classe, la descrizione comando visualizzata sopra il nome della proprietà, è simile all'estensione di proprietà naturale, in modo che il nome della proprietà è completamente visibile.  
  
 MFC automaticamente questo controllo viene creato e utilizzato nel [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come costruire un oggetto della `CMFCPropertyGridToolTipCtrl` classe e come visualizzare il controllo tooltip.  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxpropertygridtooltipctrl.h  
  
##  <a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 Costruisce un oggetto `CMFCPropertyGridToolTipCtrl`.  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="create"></a>CMFCPropertyGridToolTipCtrl::Create  
 Crea una finestra per il controllo tooltip.  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `pWndParent`  
 Puntatore alla finestra padre.  
  
### <a name="return-value"></a>Valore restituito  
 TRUE se la finestra è stata creata correttamente; in caso contrario, FALSE.  
  
##  <a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deactivate  
 Disattiva e nasconde il controllo tooltip.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Note  
 Questo metodo imposta la posizione e testo ultimo i valori vuoti, in modo che le chiamate successive al [CMFCPropertyGridToolTipCtrl::Track](#track) visualizzazione della descrizione comando.  
  
##  <a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect  
 Restituisce le coordinate dell'ultima posizione del controllo tooltip.  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [out] `rect`  
 Contiene l'ultima posizione del controllo tooltip.  
  
##  <a name="hide"></a>CMFCPropertyGridToolTipCtrl::Hide  
 Nasconde il controllo tooltip.  
  
```  
void Hide();
```  
  
##  <a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin  
 Imposta la spaziatura tra il testo della descrizione comando e il bordo della finestra della descrizione comando.  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nTextMargin`  
 Specifica la spaziatura tra il testo del controllo descrizione comando e il bordo della finestra della descrizione comando. Il valore predefinito è 10 pixel.  
  
##  <a name="track"></a>CMFCPropertyGridToolTipCtrl::Track  
 Visualizza il controllo descrizione comando.  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `rect`  
 Specifica la posizione e le dimensioni del controllo tooltip.  
  
 [in] `strText`  
 Specifica il testo da visualizzare nella descrizione comando.  
  
### <a name="remarks"></a>Note  
 Questo metodo visualizza il controllo tooltip la posizione e dimensioni specificate dal `rect`. Se la posizione, dimensione e testo non sono stati modificati dall'ultima volta che questo metodo è stato chiamato, questo metodo non ha alcun effetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)