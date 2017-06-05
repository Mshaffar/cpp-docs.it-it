---
title: Classe COleDropTarget | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
dev_langs:
- C++
helpviewer_keywords:
- COleDropTarget class
- drag and drop, drop target
- drop commands, accepting
- drop commands
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
caps.latest.revision: 23
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
ms.openlocfilehash: 0e9429d531d6af86bc571b1f871fbcd4a8fe2532
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="coledroptarget-class"></a>Classe COleDropTarget
Fornisce il meccanismo di comunicazione tra una finestra e le librerie OLE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class COleDropTarget : public CCmdTarget  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[COleDropTarget::COleDropTarget](#coledroptarget)|Costruisce un oggetto `COleDropTarget`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[COleDropTarget::OnDragEnter](#ondragenter)|Chiamato quando il cursore nella prima finestra.|  
|[COleDropTarget::OnDragLeave](#ondragleave)|Chiamato quando il cursore viene trascinato all'esterno di finestra.|  
|[COleDropTarget::OnDragOver](#ondragover)|Chiamato ripetutamente quando il cursore viene trascinato nella finestra.|  
|[COleDropTarget::OnDragScroll](#ondragscroll)|Chiamato per determinare se il cursore viene trascinato nell'area di scorrimento della finestra.|  
|[COleDropTarget::OnDrop](#ondrop)|Chiamato quando viene eliminati dati nella finestra del gestore predefinito.|  
|[COleDropTarget::OnDropEx](#ondropex)|Chiamato quando viene eliminati dati nella finestra, gestore iniziale.|  
|[COleDropTarget::Register](#register)|Registra la finestra come destinazione di rilascio valido.|  
|[COleDropTarget::Revoke](#revoke)|Fa sì che la finestra quale terminare l'operazione da una destinazione di rilascio valido.|  
  
## <a name="remarks"></a>Note  
 Creazione di un oggetto di questa classe consente a una finestra accettare i dati tramite il meccanismo di trascinamento e rilascio OLE.  
  
 Per ottenere una finestra per accettare i comandi di menu, è necessario creare prima un oggetto di `COleDropTarget` classe e quindi chiamare il [registrare](#register) funzione con un puntatore all'oggetto desiderato `CWnd` oggetto come unico parametro.  
  
 Per ulteriori informazioni sulle operazioni di trascinamento e rilascio tramite OLE, vedere l'articolo [trascinamento della selezione (OLE)](../../mfc/drag-and-drop-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDropTarget`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** AFXOLE. h  
  
##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget  
 Costruisce un oggetto della classe `COleDropTarget`.  
  
```  
COleDropTarget();
```  
  
### <a name="remarks"></a>Note  
 Chiamare [registrare](#register) per associare l'oggetto a una finestra.  
  
##  <a name="ondragenter"></a>COleDropTarget::OnDragEnter  
 Chiamato dal framework quando il cursore viene prima trascinato nella finestra.  
  
```  
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametri  
 `pWnd`  
 Punta alla finestra che passa il cursore.  
  
 `pDataObject`  
 Punta all'oggetto dati che contiene i dati che possono essere eliminati.  
  
 `dwKeyState`  
 Contiene lo stato dei tasti di modifica. Si tratta di una combinazione di un numero qualsiasi di quanto segue: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, e **MK_RBUTTON**.  
  
 `point`  
 Contiene il percorso corrente del cursore nelle coordinate client.  
  
### <a name="return-value"></a>Valore restituito  
 L'effetto che risulterebbe se tentata un'eliminazione nella posizione specificata da `point`. Può trattarsi di uno o più delle seguenti operazioni:  
  
- `DROPEFFECT_NONE`Un rilascio non sarebbe consentito.  
  
- `DROPEFFECT_COPY`Verrà eseguita un'operazione di copia.  
  
- `DROPEFFECT_MOVE`Verrà eseguita un'operazione di spostamento.  
  
- `DROPEFFECT_LINK`Potrebbe essere stabilito un collegamento dai dati eliminati i dati originali.  
  
- `DROPEFFECT_SCROLL`Un'operazione di trascinamento scorrimento sta per verificarsi o si verifica nel database di destinazione.  
  
### <a name="remarks"></a>Note  
 Eseguire l'override di questa funzione per consentire operazioni di eliminazione si verificano nella finestra. L'implementazione predefinita chiama [CView::OnDragEnter](../../mfc/reference/cview-class.md#ondragenter), che restituisce semplicemente `DROPEFFECT_NONE` per impostazione predefinita.  
  
 Per ulteriori informazioni, vedere [IDropTarget::DragEnter](http://msdn.microsoft.com/library/windows/desktop/ms680106) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondragleave"></a>COleDropTarget::OnDragLeave  
 Chiamato dal framework quando il cursore lascia la finestra mentre è in corso un'operazione di trascinamento.  
  
```  
virtual void OnDragLeave(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametri  
 `pWnd`  
 Punta alla finestra che si sta spostando il cursore.  
  
### <a name="remarks"></a>Note  
 Eseguire l'override di questa funzione se si desidera un comportamento speciale quando l'operazione di trascinamento rende la finestra specificata. L'implementazione predefinita di questa funzione chiama [CView::OnDragLeave](../../mfc/reference/cview-class.md#ondragleave).  
  
 Per ulteriori informazioni, vedere [IDropTarget::DragLeave](http://msdn.microsoft.com/library/windows/desktop/ms680110) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondragover"></a>COleDropTarget::OnDragOver  
 Chiamato dal framework quando il cursore viene trascinato nella finestra.  
  
```  
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametri  
 `pWnd`  
 Punta alla finestra che il cursore è posizionato.  
  
 `pDataObject`  
 Punta all'oggetto dati che contiene i dati da eliminare.  
  
 `dwKeyState`  
 Contiene lo stato dei tasti di modifica. Si tratta di una combinazione di un numero qualsiasi di quanto segue: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, e **MK_RBUTTON**.  
  
 `point`  
 Contiene il percorso corrente del cursore nelle coordinate client.  
  
### <a name="return-value"></a>Valore restituito  
 L'effetto che risulterebbe se tentata un'eliminazione nella posizione specificata da `point`. Può trattarsi di uno o più delle seguenti operazioni:  
  
- `DROPEFFECT_NONE`Un rilascio non sarebbe consentito.  
  
- `DROPEFFECT_COPY`Verrà eseguita un'operazione di copia.  
  
- `DROPEFFECT_MOVE`Verrà eseguita un'operazione di spostamento.  
  
- `DROPEFFECT_LINK`Potrebbe essere stabilito un collegamento dai dati eliminati i dati originali.  
  
- `DROPEFFECT_SCROLL`Indica che un'operazione di trascinamento scorrimento sta per verificarsi o si verifica nel database di destinazione.  
  
### <a name="remarks"></a>Note  
 Questa funzione deve essere sottoposto a override per consentire le operazioni di eliminazione si verifichi nella finestra. L'implementazione predefinita di questa funzione chiama [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover), che restituisce `DROPEFFECT_NONE` per impostazione predefinita. Poiché questa funzione viene chiamata frequentemente durante un'operazione di trascinamento e rilascio, viene ottimizzata per quanto possibile.  
  
 Per ulteriori informazioni, vedere [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms680129) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCOleContainer numero&21;](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]  
  
##  <a name="ondragscroll"></a>COleDropTarget::OnDragScroll  
 Chiamato dal framework prima di chiamare [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) per determinare se `point` è l'area di scorrimento.  
  
```  
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametri  
 `pWnd`  
 Punta alla finestra che si trova attualmente il cursore.  
  
 `dwKeyState`  
 Contiene lo stato dei tasti di modifica. Si tratta di una combinazione di un numero qualsiasi di quanto segue: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, e **MK_RBUTTON**.  
  
 `point`  
 Contiene la posizione del cursore, in pixel, rispetto allo schermo.  
  
### <a name="return-value"></a>Valore restituito  
 L'effetto che risulterebbe se tentata un'eliminazione nella posizione specificata da `point`. Può trattarsi di uno o più delle seguenti operazioni:  
  
- `DROPEFFECT_NONE`Un rilascio non sarebbe consentito.  
  
- `DROPEFFECT_COPY`Verrà eseguita un'operazione di copia.  
  
- `DROPEFFECT_MOVE`Verrà eseguita un'operazione di spostamento.  
  
- `DROPEFFECT_LINK`Potrebbe essere stabilito un collegamento dai dati eliminati i dati originali.  
  
- `DROPEFFECT_SCROLL`Indica che un'operazione di trascinamento scorrimento sta per verificarsi o si verifica nel database di destinazione.  
  
### <a name="remarks"></a>Note  
 Eseguire l'override di questa funzione quando si desidera fornire un comportamento speciale per questo evento. L'implementazione predefinita di questa funzione chiama [CView::OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll), che restituisce `DROPEFFECT_NONE` e scorre la finestra quando il cursore viene trascinato nell'area di scorrimento predefinita all'interno del bordo della finestra.  
  
##  <a name="ondrop"></a>COleDropTarget::OnDrop  
 Chiamato dal framework quando un'operazione di trascinamento deve verificarsi.  
  
```  
virtual BOOL OnDrop(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametri  
 `pWnd`  
 Punta alla finestra che si trova attualmente il cursore.  
  
 `pDataObject`  
 Punta all'oggetto dati che contiene i dati da eliminare.  
  
 `dropEffect`  
 L'effetto che l'utente ha scelto per l'operazione di trascinamento. Può trattarsi di uno o più delle seguenti operazioni:  
  
- `DROPEFFECT_COPY`Verrà eseguita un'operazione di copia.  
  
- `DROPEFFECT_MOVE`Verrà eseguita un'operazione di spostamento.  
  
- `DROPEFFECT_LINK`Potrebbe essere stabilito un collegamento dai dati eliminati i dati originali.  
  
 `point`  
 Contiene la posizione del cursore, in pixel, rispetto allo schermo.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se l'eliminazione ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Il framework chiama prima [OnDropEx](#ondropex). Se il `OnDropEx` funzione non gestisce l'eliminazione, il framework chiama la funzione di questo membro, `OnDrop`. In genere, l'applicazione esegue l'override [OnDropEx](../../mfc/reference/cview-class.md#ondropex) nella classe di visualizzazione per la gestione del pulsante destro del mouse trascinare e rilasciare. In genere, la classe di visualizzazione [OnDrop](../../mfc/reference/cview-class.md#ondrop) viene utilizzata per gestire il semplice trascinamento.  
  
 L'implementazione predefinita di `COleDropTarget::OnDrop` chiamate [CView::OnDrop](../../mfc/reference/cview-class.md#ondrop), che restituisce semplicemente **FALSE** per impostazione predefinita.  
  
 Per ulteriori informazioni, vedere [IDropTarget:: DROP](http://msdn.microsoft.com/library/windows/desktop/ms687242) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondropex"></a>COleDropTarget::OnDropEx  
 Chiamato dal framework quando un'operazione di trascinamento deve verificarsi.  
  
```  
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,  
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parametri  
 `pWnd`  
 Punta alla finestra che si trova attualmente il cursore.  
  
 `pDataObject`  
 Punta all'oggetto dati che contiene i dati da eliminare.  
  
 `dropDefault`  
 L'effetto che l'utente ha scelto per l'operazione di eliminazione predefinito in base allo stato di chiave corrente. Può essere `DROPEFFECT_NONE`. Effetti di trascinamento sono descritti nella sezione Osservazioni.  
  
 `dropList`  
 Un elenco degli effetti di trascinamento che supporta l'origine del trascinamento. I valori di effetto di rilascio possono essere combinati utilizzando l'operatore OR bit per bit ( **|**) operazione. Effetti di trascinamento sono descritti nella sezione Osservazioni.  
  
 `point`  
 Contiene la posizione del cursore, in pixel, rispetto allo schermo.  
  
### <a name="return-value"></a>Valore restituito  
 L'effetto che ha causato dal tentativo di eliminazione nella posizione specificata da `point`. Effetti di trascinamento sono descritti nella sezione Osservazioni.  
  
### <a name="remarks"></a>Note  
 Innanzitutto, il framework chiama questa funzione. Se non viene gestito l'eliminazione, il framework chiama [OnDrop](#ondrop). In genere, si eseguirà l'override [OnDropEx](../../mfc/reference/cview-class.md#ondropex) nella classe di visualizzazione per il supporto del pulsante destro del mouse trascinare e rilasciare. In genere, la classe di visualizzazione [OnDrop](../../mfc/reference/cview-class.md#ondrop) viene utilizzato per gestire il caso di supporto per il semplice trascinamento.  
  
 L'implementazione predefinita di `COleDropTarget::OnDropEx` chiamate [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex). Per impostazione predefinita, [CView::OnDropEx](../../mfc/reference/cview-class.md#ondropex) restituisce semplicemente un valore fittizio per indicare il [OnDrop](#ondrop) funzione membro deve essere chiamata.  
  
 Effetti di trascinamento viene descritta l'azione associata a un'operazione di trascinamento. Vedere il seguente elenco di effetti di trascinamento:  
  
- `DROPEFFECT_NONE`Un rilascio non sarebbe consentito.  
  
- `DROPEFFECT_COPY`Verrà eseguita un'operazione di copia.  
  
- `DROPEFFECT_MOVE`Verrà eseguita un'operazione di spostamento.  
  
- `DROPEFFECT_LINK`Potrebbe essere stabilito un collegamento dai dati eliminati i dati originali.  
  
- `DROPEFFECT_SCROLL`Indica che un'operazione di trascinamento scorrimento sta per verificarsi o si verifica nel database di destinazione.  
  
 Per ulteriori informazioni, vedere [IDropTarget:: DROP](http://msdn.microsoft.com/library/windows/desktop/ms687242) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="register"></a>COleDropTarget::Register  
 Chiamare questa funzione per registrare la finestra con le DLL OLE come destinazione di rilascio valido.  
  
```  
BOOL Register(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametri  
 `pWnd`  
 Punta alla finestra che deve essere registrato come destinazione di trascinamento.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se la registrazione ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Questa funzione deve essere chiamata per le operazioni di eliminazione di essere accettati.  
  
 Per ulteriori informazioni, vedere [RegisterDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms678405) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="revoke"></a>COleDropTarget::Revoke  
 Chiamare questa funzione prima di eliminare tutte le finestre che sono stata registrata come destinazione di trascinamento tramite una chiamata a [registrare](#register) per rimuoverlo dall'elenco delle destinazioni di rilascio.  
  
```  
virtual void Revoke();
```  
  
### <a name="remarks"></a>Note  
 Questa funzione viene chiamata automaticamente dal [OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy) gestore per la finestra che è stata registrata, pertanto non è in genere necessario chiamare questa funzione in modo esplicito.  
  
 Per ulteriori informazioni, vedere [RevokeDragDrop](http://msdn.microsoft.com/library/windows/desktop/ms692643) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio HIERSVR](../../visual-cpp-samples.md)   
 [Esempio MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classe COleDropSource](../../mfc/reference/coledropsource-class.md)
