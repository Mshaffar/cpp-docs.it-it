---
title: Classe COleServerDoc | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
dev_langs:
- C++
helpviewer_keywords:
- servers, OLE
- OLE server applications, managing server documents
- container/server applications
- OLE server documents
- COleServerDoc class
- server documents, OLE
- OLE containers, server documents
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
caps.latest.revision: 24
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: db50c2a5709fbc07d0e0db99a4cffc733c4b6ead
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="coleserverdoc-class"></a>Classe COleServerDoc
Classe di base per i documenti del server OLE.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Costruisce un oggetto `COleServerDoc`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Attiva il documento associato DocObject.|  
|[COleServerDoc::ActivateInPlace](#activateinplace)|Attiva il documento per la modifica sul posto.|  
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Disattiva interfaccia utente del server.|  
|[COleServerDoc::DiscardUndoState](#discardundostate)|Elimina le informazioni sullo stato di annullamento.|  
|[COleServerDoc::GetClientSite](#getclientsite)|Recupera un puntatore all'oggetto sottostante `IOleClientSite` interfaccia.|  
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Restituisce un puntatore a un elemento che rappresenta l'intero documento.|  
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Restituisce il rettangolo di ritaglio corrente per la modifica sul posto.|  
|[COleServerDoc::GetItemPosition](#getitemposition)|Restituisce il rettangolo di posizione corrente, rispetto all'area client dell'applicazione contenitore, per la modifica sul posto.|  
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Restituisce il fattore di zoom in pixel.|  
|[COleServerDoc::IsDocObject](#isdocobject)|Determina se il documento è DocObject.|  
|[COleServerDoc::IsEmbedded](#isembedded)|Indica se il documento è in esecuzione autonomo o incorporato in un documento contenitore.|  
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Restituisce `TRUE` se l'elemento è attualmente attivato sul posto.|  
|[COleServerDoc::NotifyChanged](#notifychanged)|Notifica contenitori che l'utente ha modificato il documento.|  
|[COleServerDoc::NotifyClosed](#notifyclosed)|Notifica contenitori che l'utente ha chiuso il documento.|  
|[COleServerDoc::NotifyRename](#notifyrename)|Notifica contenitori che l'utente ha rinominato il documento.|  
|[COleServerDoc::NotifySaved](#notifysaved)|Notifica contenitori che l'utente ha salvato il documento.|  
|[COleServerDoc::OnDeactivate](#ondeactivate)|Chiamato dal framework quando l'utente disattiva un elemento che è stato attivato sul posto.|  
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Chiamato dal framework per distruggere i controlli e altri elementi dell'interfaccia utente creati per l'attivazione sul posto.|  
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Chiamato dal framework quando finestra cornice di documento del contenitore è attivata o disattivata.|  
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Chiamato dal framework quando viene ridimensionata una finestra cornice o finestra del documento dell'applicazione contenitore.|  
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Chiamato dal framework per mostrare o nascondere le barre di controllo per la modifica sul posto.|  
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Chiamato dal framework quando viene salvato un documento nel server è un elemento incorporato, l'aggiornamento di copia del contenitore dell'elemento.|  
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Modifica la posizione della cornice per la modifica sul posto.|  
|[COleServerDoc::SaveEmbedding](#saveembedding)|Indica all'applicazione contenitore per salvare il documento.|  
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Scorre il documento contenitore.|  
|[COleServerDoc::UpdateAllItems](#updateallitems)|Notifica contenitori che l'utente ha modificato il documento.|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Chiamato dal framework per creare una finestra cornice per la modifica sul posto.|  
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Chiamato dal framework per eliminare una finestra cornice per la modifica sul posto.|  
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Eseguire l'override di questa funzione per creare un nuovo `CDocObjectServer` dell'oggetto e indicare che il documento è un contenitore DocObject.|  
|[COleServerDoc::OnClose](#onclose)|Chiamato dal framework quando un contenitore richiede la chiusura del documento.|  
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Esegue un comando specificato o viene visualizzata la Guida per il comando.|  
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Chiamato dal framework quando una finestra cornice del contenitore è attivata o disattivata.|  
|[COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem)|Chiamato per ottenere un `COleServerItem` che rappresenta l'intero documento, utilizzata per ottenere un elemento incorporato. Implementazione necessaria.|  
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Chiamato dal framework per annullare le modifiche apportate durante la modifica sul posto.|  
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Chiamato dal framework quando un contenitore imposta il titolo della finestra per un oggetto incorporato.|  
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Chiamato dal framework per posizionare la finestra cornice modifica sul posto all'interno di finestra dell'applicazione contenitore.|  
|[COleServerDoc::OnShowDocument](#onshowdocument)|Chiamato dal framework per mostrare o nascondere il documento.|  
  
## <a name="remarks"></a>Note  
 Può contenere un documento server [COleServerItem](../../mfc/reference/coleserveritem-class.md) gli oggetti che rappresentano l'interfaccia server agli elementi incorporati o collegati. Quando un'applicazione server viene avviata da un contenitore per modificare un elemento incorporato, l'elemento viene caricato come il proprio documento server. il `COleServerDoc` oggetto contiene solo una `COleServerItem` oggetto, l'intero documento. Quando un'applicazione server viene avviata da un contenitore per modificare un elemento collegato, un documento esistente viene caricato dal disco. una parte del contenuto del documento è evidenziata per indicare che l'elemento collegato.  
  
 `COleServerDoc`gli oggetti possono inoltre contenere elementi del [COleClientItem](../../mfc/reference/coleclientitem-class.md) (classe). Ciò consente di creare applicazioni contenitore / server. Il framework fornisce funzioni per archiviare in modo corretto il `COleClientItem` elementi durante la gestione di `COleServerItem` oggetti.  
  
 Se l'applicazione server non supporta i collegamenti, un documento server conterrà sempre un solo elemento del server, che rappresenta l'intero oggetto incorporato come un documento. Se l'applicazione server supporta i collegamenti, è necessario creare un elemento del server ogni volta che una selezione viene copiata negli Appunti.  
  
 Utilizzare `COleServerDoc`, derivare una classe e implementare il [OnGetEmbeddedItem](#ongetembeddeditem) funzione membro, che consente al server supportare gli elementi incorporati. Derivare una classe da `COleServerItem` per implementare gli elementi nei documenti e restituire oggetti di tale classe da `OnGetEmbeddedItem`.  
  
 Per supportare gli elementi collegati, `COleServerDoc` fornisce il [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) funzione membro. È possibile utilizzare l'implementazione predefinita o sostituirlo se è possibile personalizzare le modalità di gestione degli elementi del documento.  
  
 È necessario utilizzare un `COleServerDoc`-classe derivata per ogni tipo di server di documenti supportate dall'applicazione. Ad esempio, se l'applicazione server supporta i grafici e fogli di lavoro, è necessario due `COleServerDoc`-classi derivate.  
  
 Per ulteriori informazioni sui server, vedere l'articolo [server: implementazione di un Server](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** AFXOLE. h  
  
##  <a name="activatedocobject"></a>COleServerDoc::ActivateDocObject  
 Attiva il documento associato DocObject.  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Note  
 Per impostazione predefinita, `COleServerDoc` non supporta i documenti attivi (nota anche come DocObjects). Per abilitare questo supporto, vedere [GetDocObjectServer](#getdocobjectserver) e classe [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).  
  
##  <a name="activateinplace"></a>COleServerDoc::ActivateInPlace  
 Attiva l'elemento per la modifica sul posto.  
  
```  
BOOL ActivateInPlace();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo. in caso contrario, 0, che indica che l'elemento è completamente aperto.  
  
### <a name="remarks"></a>Note  
 Questa funzione esegue tutte le operazioni necessarie per l'attivazione sul posto. Crea una finestra cornice sul posto, viene attivato e viene ridimensionata per l'elemento, configura condivisi menu e altri controlli, scorre l'elemento nella visualizzazione e imposta lo stato attivo alla finestra cornice sul posto.  
  
 Questa funzione viene chiamata dall'implementazione predefinita di [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Chiamare questa funzione se l'applicazione supporta un altro verbo per l'attivazione sul posto (ad esempio Play).  
  
##  <a name="coleserverdoc"></a>COleServerDoc::COleServerDoc  
 Costruisce un `COleServerDoc` oggetto senza eseguire la connessione con le DLL di sistema OLE.  
  
```  
COleServerDoc();
```  
  
### <a name="remarks"></a>Note  
 È necessario chiamare [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) per aprire le comunicazioni con OLE. Se si utilizza [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) nell'applicazione, `COleLinkingDoc::Register` viene chiamato automaticamente da `COleLinkingDoc`dell'implementazione di `OnNewDocument`, `OnOpenDocument`, e `OnSaveDocument`.  
  
##  <a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame  
 Il framework chiama questa funzione per creare una finestra cornice per la modifica sul posto.  
  
```  
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parametri  
 `pParentWnd`  
 Puntatore alla finestra padre dell'applicazione contenitore.  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore alla finestra cornice sul posto o **NULL** in caso contrario.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita utilizza le informazioni specificate nel modello di documento per creare la cornice. La visualizzazione utilizzata è la prima vista creata per il documento. In questa vista viene temporaneamente dal frame originale collegata o scollegata al frame appena creato.  
  
 Questa è un' sottoponibile a override.  
  
##  <a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo  
 Chiamare questa funzione se annullare supportate dall'applicazione e l'utente sceglie Annulla dopo l'attivazione di un elemento ma prima di modificarlo.  
  
```  
BOOL DeactivateAndUndo();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero in caso di esito positivo; in caso contrario, 0.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione determina se l'applicazione contenitore viene scritta utilizzando la libreria Microsoft Foundation Class, [COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) da chiamare, che disattiva l'interfaccia utente del server.  
  
##  <a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame  
 Il framework chiama questa funzione per eliminare una finestra cornice sul posto e riportare il server di finestra del documento dell'applicazione allo stato prima dell'attivazione sul posto.  
  
```  
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>Parametri  
 `pFrameWnd`  
 Puntatore alla finestra cornice sul posto di essere eliminati.  
  
### <a name="remarks"></a>Note  
 Questa è un' sottoponibile a override.  
  
##  <a name="discardundostate"></a>COleServerDoc::DiscardUndoState  
 Se l'utente esegue un'operazione di modifica che non può essere annullata, chiamare questa funzione per forzare l'applicazione contenitore per ignorare le informazioni sullo stato di annullamento.  
  
```  
BOOL DiscardUndoState();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero in caso di esito positivo; in caso contrario, 0.  
  
### <a name="remarks"></a>Note  
 Questa funzione viene fornita in modo che i server che supportano l'annullamento possono liberare le risorse che altrimenti sarebbero utilizzabile dalle informazioni sullo stato di annullamento che non possono essere utilizzate.  
  
##  <a name="getclientsite"></a>COleServerDoc::GetClientSite  
 Recupera un puntatore all'oggetto sottostante `IOleClientSite` interfaccia.  
  
```  
LPOLECLIENTSITE GetClientSite() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Recupera un puntatore all'oggetto sottostante [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706) interfaccia.  
  
##  <a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer  
 Eseguire l'override di questa funzione per creare un nuovo `CDocObjectServer` elemento e restituire un puntatore ad esso.  
  
```  
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```  
  
### <a name="parameters"></a>Parametri  
 `pDocSite`  
 Puntatore al `IOleDocumentSite` interfaccia che si connetterà il server di questo documento.  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore a un `CDocObjectServer`; **NULL** se l'operazione non riuscita.  
  
### <a name="remarks"></a>Note  
 Quando viene attivato un server DocObject, la restituzione di un non - **NULL** puntatore mostra che il client può supportare DocObjects. L'implementazione predefinita restituisce **NULL**.  
  
 Un'implementazione tipica di un documento che supporta DocObjects semplicemente verrà allocata una nuova `CDocObjectServer` dell'oggetto e restituirlo al chiamante. Ad esempio:  
  
 [!code-cpp[NVC_MFCOleServer n.&3;](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]  
  
##  <a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem  
 Chiamare questa funzione per ottenere un puntatore a un elemento che rappresenta l'intero documento.  
  
```  
COleServerItem* GetEmbeddedItem();
```  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore a un elemento che rappresenta il documento. **NULL** se l'operazione non riuscita.  
  
### <a name="remarks"></a>Note  
 Chiama [COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem), una funzione virtuale senza l'implementazione predefinita.  
  
##  <a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect  
 Chiamare il `GetItemClipRect` funzione membro per ottenere le coordinate del rettangolo di ridimensionamento dell'elemento che viene modificato sul posto.  
  
```  
void GetItemClipRect(LPRECT lpClipRect) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `lpClipRect`  
 Puntatore a un `RECT` struttura o un `CRect` oggetto per ricevere le coordinate del rettangolo di ridimensionamento dell'elemento.  
  
### <a name="remarks"></a>Note  
 Le coordinate sono espresse in pixel rispetto all'area client della finestra dell'applicazione contenitore.  
  
 Disegno non viene eseguito all'esterno del rettangolo di ritaglio. Disegno in genere, viene automaticamente limitato. Utilizzare questa funzione per determinare se l'utente è stata fatta scorrere all'esterno la parte visibile del documento. In questo caso, scorrere il documento contenitore in base alle esigenze mediante una chiamata a [ScrollContainerBy](#scrollcontainerby).  
  
##  <a name="getitemposition"></a>COleServerDoc::GetItemPosition  
 Chiamare il `GetItemPosition` funzione membro per ottenere le coordinate dell'elemento viene modificata sul posto.  
  
```  
void GetItemPosition(LPRECT lpPosRect) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `lpPosRect`  
 Puntatore a un `RECT` struttura o un `CRect` oggetto per ricevere le coordinate dell'elemento.  
  
### <a name="remarks"></a>Note  
 Le coordinate sono espresse in pixel rispetto all'area client della finestra dell'applicazione contenitore.  
  
 La posizione dell'elemento può essere confrontata con il rettangolo di ritaglio corrente per determinare l'entità a cui l'elemento è visibile (o meno) sullo schermo.  
  
##  <a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor  
 Il `GetZoomFactor` funzione membro determina il "fattore di zoom" di un elemento che è stato attivato per la modifica sul posto.  
  
```  
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,  
    LPSIZE lpSizeDenom = NULL,  
    LPCRECT lpPosRect = NULL) const;  
```  
  
### <a name="parameters"></a>Parametri  
 *lpSizeNum*  
 Puntatore a un oggetto della classe `CSize` che conterrà il numeratore del fattore di zoom. Può essere **NULL**.  
  
 *lpSizeDenom*  
 Puntatore a un oggetto della classe `CSize` che conterrà il denominatore del fattore di zoom. Può essere **NULL**.  
  
 `lpPosRect`  
 Puntatore a un oggetto della classe `CRect` che descrive la nuova posizione. Se questo argomento è **NULL**, la funzione utilizza la posizione dell'elemento corrente.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se l'elemento viene attivato sul posto per la modifica e il fattore di zoom è è diverso da 100% (1:1); in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Il fattore di zoom, in pixel, è la percentuale delle dimensioni dell'elemento di estensione corrente. Se l'applicazione contenitore non è impostata la misura dell'articolo, estensione naturale (come determinato dalla [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) viene utilizzato.  
  
 La funzione imposta i primi due argomenti per il numeratore e del denominatore di "fattore di zoom." dell'elemento Se l'elemento non viene modificato sul posto, la funzione imposta questi argomenti per un valore predefinito di 100% (o 1:1) e restituisce zero. Per ulteriori informazioni, vedere 40 Nota tecnica, [il ridimensionamento di MFC/OLE sul posto e zoom](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).  
  
##  <a name="isdocobject"></a>COleServerDoc::IsDocObject  
 Determina se il documento è DocObject.  
  
```  
BOOL IsDocObject() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 **TRUE** se il documento è DocObject; in caso contrario **FALSE**.  
  
##  <a name="isembedded"></a>COleServerDoc::IsEmbedded  
 Chiamare il `IsEmbedded` funzione membro per determinare se il documento rappresenta un oggetto incorporato in un contenitore.  
  
```  
BOOL IsEmbedded() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se la `COleServerDoc` oggetto è un documento che rappresenta un oggetto incorporato in un contenitore; in caso contrario, 0.  
  
### <a name="remarks"></a>Note  
 Un documento caricato da un file non è incorporato anche se possono essere modificati da un'applicazione contenitore come collegamento. Deve essere incorporato viene considerato un documento incorporato in un documento contenitore.  
  
##  <a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive  
 Chiamare il `IsInPlaceActive` funzione membro per determinare se l'elemento è attualmente in stato attivo sul posto.  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se la `COleServerDoc` oggetto è attivo sul posto; in caso contrario, 0.  
  
##  <a name="notifychanged"></a>COleServerDoc::NotifyChanged  
 Chiamare questa funzione per notificare a tutti gli elementi collegati collegati al documento che è stato modificato il documento.  
  
```  
void NotifyChanged();
```  
  
### <a name="remarks"></a>Note  
 In genere, si chiama questa funzione dopo che l'utente modifica un attributo globale, ad esempio le dimensioni del documento server. Se un elemento OLE è collegato al documento con un collegamento automatico, l'elemento viene aggiornato per riflettere le modifiche. Nelle applicazioni contenitore scritte con la libreria Microsoft Foundation Class di [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funzione membro `COleClientItem` viene chiamato.  
  
> [!NOTE]
>  Questa funzione è inclusa per compatibilità con OLE 1. Nuove applicazioni devono utilizzare [UpdateAllItems](#updateallitems).  
  
##  <a name="notifyclosed"></a>COleServerDoc::NotifyClosed  
 Chiamare questa funzione per notificare il contenitore che il documento è stata chiusa.  
  
```  
void NotifyClosed();
```  
  
### <a name="remarks"></a>Note  
 Quando l'utente sceglie il comando Chiudi dal menu File, `NotifyClosed` viene chiamato da `COleServerDoc`dell'implementazione di [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) funzione membro. Nelle applicazioni contenitore scritte con la libreria Microsoft Foundation Class di [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funzione membro `COleClientItem` viene chiamato.  
  
##  <a name="notifyrename"></a>COleServerDoc::NotifyRename  
 Chiamare questa funzione dopo che l'utente rinomina il documento server.  
  
```  
void NotifyRename(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszNewName`  
 Puntatore a una stringa che specifica il nuovo nome del documento server. Questo è in genere il percorso completo.  
  
### <a name="remarks"></a>Note  
 Quando l'utente sceglie il comando Salva con nome dal menu File, `NotifyRename` viene chiamato da `COleServerDoc`dell'implementazione di [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) funzione membro. Questa funzione notifica DLL, che a sua volta notifica i contenitori OLE di sistema. Nelle applicazioni contenitore scritte con la libreria Microsoft Foundation Class di [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funzione membro `COleClientItem` viene chiamato.  
  
##  <a name="notifysaved"></a>COleServerDoc::NotifySaved  
 Chiamare questa funzione dopo che l'utente salva il documento server.  
  
```  
void NotifySaved();
```  
  
### <a name="remarks"></a>Note  
 Quando l'utente sceglie il comando Salva dal menu File, `NotifySaved` viene chiamato automaticamente da `COleServerDoc`dell'implementazione di [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Questa funzione notifica DLL, che a sua volta notifica i contenitori OLE di sistema. Nelle applicazioni contenitore scritte con la libreria Microsoft Foundation Class di [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funzione membro `COleClientItem` viene chiamato.  
  
##  <a name="onclose"></a>COleServerDoc::OnClose  
 Chiamato dal framework quando un contenitore richiede che il documento server venga chiusa.  
  
```  
virtual void OnClose(OLECLOSE dwCloseOption);
```  
  
### <a name="parameters"></a>Parametri  
 `dwCloseOption`  
 Un valore dall'enumerazione `OLECLOSE`. Per il parametro è possibile specificare uno dei valori riportati di seguito:  
  
- `OLECLOSE_SAVEIFDIRTY`Se è stato modificato, il file viene salvato.  
  
- `OLECLOSE_NOSAVE`Il file viene chiuso senza eseguirne il salvataggio.  
  
- `OLECLOSE_PROMPTSAVE`Se il file è stato modificato, l'utente viene richiesto di salvarlo.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita chiama `CDocument::OnCloseDocument`.  
  
 Per ulteriori informazioni e i valori aggiuntivi, vedere [OLECLOSE](http://msdn.microsoft.com/library/windows/desktop/ms680623) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondeactivate"></a>COleServerDoc::OnDeactivate  
 Chiamato dal framework quando l'utente disattiva un elemento incorporato o collegato che è attualmente attiva.  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>Note  
 Questa funzione consente di ripristinare lo stato originale dell'interfaccia utente dell'applicazione contenitore ed Elimina tutti i menu e altri controlli che sono stati creati per l'attivazione sul posto.  
  
 Le informazioni sullo stato di annullamento devono essere liberate una in modo incondizionato a questo punto.  
  
 Per ulteriori informazioni, vedere l'articolo [attivazione](../../mfc/activation-cpp.md)...  
  
##  <a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI  
 Chiamato quando l'utente disattiva un elemento che è stato attivato sul posto.  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>Parametri  
 `bUndoable`  
 Specifica se le modifiche possono essere annullate.  
  
### <a name="remarks"></a>Note  
 Questa funzione consente di ripristinare lo stato originale, nascondere tutti i menu e altri controlli che sono stati creati per l'attivazione sul posto dell'interfaccia utente dell'applicazione contenitore.  
  
 Il framework imposta sempre `bUndoable` a **FALSE**. Se il server supporta l'annullamento ed è presente un'operazione che può essere annullata, chiamare l'implementazione della classe base con `bUndoable` impostato su **TRUE**.  
  
##  <a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate  
 Il framework chiama questa funzione per attivare o disattivare una finestra del documento per la modifica sul posto.  
  
```  
virtual void OnDocWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametri  
 `bActivate`  
 Specifica se la finestra del documento deve essere attivata o disattivata.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita rimuove o aggiunge gli elementi dell'interfaccia utente a livello di frame come appropriato. Eseguire l'override di questa funzione se si desidera eseguire azioni aggiuntive quando il documento contenente l'elemento viene attivato o disattivato.  
  
 Per ulteriori informazioni, vedere l'articolo [attivazione](../../mfc/activation-cpp.md)...  
  
##  <a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd  
 Il framework chiama questa funzione per visualizzare la Guida per il comando o eseguire un comando specificato.  
  
```  
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,  
    DWORD nCmdID,  
    DWORD nCmdExecOpt,  
    VARIANTARG* pvarargIn,  
    VARIANTARG* pvarargOut);
```  
  
### <a name="parameters"></a>Parametri  
 `pguidCmdGroup`  
 Un puntatore a un GUID che identifica un set di comandi. Può essere **NULL** per indicare il gruppo di comando predefinito.  
  
 `nCmdID`  
 Comando da eseguire. È necessario appartenere al gruppo identificato da `pguidCmdGroup`.  
  
 *nCmdExecOut*  
 Il modo l'oggetto deve eseguire il comando, uno o più dei seguenti valori di **OLECMDEXECOPT** enumerazione:  
  
 **OLECMDEXECOPT_DODEFAULT**  
  
 **OLECMDEXECOPT_PROMPTUSER**  
  
 **OLECMDEXECOPT_DONTPROMPTUSER**  
  
 **OLECMDEXECOPT_SHOWHELP**  
  
 `pvarargIn`  
 Puntatore a un **VARIANTARG** contenente gli argomenti di input per il comando. Può essere **NULL**.  
  
 `pvarargOut`  
 Puntatore a un **VARIANTARG** per ricevere i valori restituiti di output del comando. Può essere **NULL**.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo; in caso contrario, uno dei seguenti codici di errore:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Errore imprevisto|  
|**E_FAIL**|Errore|  
|**E_NOTIMPL**|Indica MFC stessa deve tentare di tradurre e inviare il comando|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`è diverso da **NULL** ma non specifica un gruppo di comando riconosciuto|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`non è riconosciuto come un comando valido nel gruppo`pguidCmdGroup`|  
|**OLECMDERR_DISABLED**|Il comando identificato da `nCmdID` è disabilitato e non può essere eseguita|  
|**OLECMDERR_NOHELP**|Chiamante richiesto per la Guida sul comando identificato da `nCmdID` ma non sono disponibili informazioni|  
|**OLECMDERR_CANCELED**|Esecuzione annullata dall'utente|  
  
### <a name="remarks"></a>Note  
 `COleCmdUI`Consente di abilitare, aggiornare e impostare altre proprietà dei comandi dell'interfaccia utente DocObject. Dopo i comandi vengono inizializzati, è possibile eseguirle con `OnExecOleCmd`.  
  
 Il framework chiama la funzione prima di tentare di tradurre e invierà un comando di documento OLE. Non è necessario eseguire l'override della funzione per gestire i comandi standard di documenti OLE, ma è necessario fornire un override di questa funzione se si desidera gestire comandi personalizzati o per gestire i comandi che accettano parametri o restituiranno i risultati.  
  
 La maggior parte dei comandi non accettano argomenti o valori restituiti. Per la maggior parte dei comandi il chiamante può passare **NULL**s per `pvarargIn` e `pvarargOut`. Per i comandi che prevede valori di input, il chiamante può dichiarare e inizializzare un **VARIANTARG** variabile e passare un puntatore alla variabile in `pvarargIn`. Per i comandi che richiedono un singolo valore, l'argomento può essere archiviato direttamente nella **VARIANTARG** e passato alla funzione. Più argomenti devono essere inseriti nel **VARIANTARG** utilizzando uno dei tipi supportati (ad esempio `IDispatch` e **SAFEARRAY** ).  
  
 Analogamente, se un comando restituisce argomenti il chiamante deve dichiarare un **VARIANTARG**, inizializzarla su `VT_EMPTY`e passare l'indirizzo in `pvarargOut`. Se un comando restituisce un singolo valore, tale valore direttamente in è possibile memorizzare nell'oggetto `pvarargOut`. Più valori di output devono essere incluso in un pacchetto in modo appropriato per il **VARIANTARG**.  
  
 Verrà illustrata l'implementazione della classe di base di questa funzione il **OLE_COMMAND_MAP** strutture associate alla destinazione del comando e provare a inviare il comando per un gestore appropriato. L'implementazione della classe di base funziona solo con i comandi che non accettano argomenti o valori restituiti. Se è necessario gestire i comandi che accettano argomenti o valori restituiti, è necessario eseguire l'override di questa funzione e lavorare con il `pvarargIn` e `pvarargOut` i parametri manualmente.  
  
##  <a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate  
 Il framework chiama questa funzione quando viene attivata o disattivata una finestra cornice dell'applicazione contenitore.  
  
```  
virtual void OnFrameWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametri  
 `bActivate`  
 Specifica se la finestra cornice deve essere attivata o disattivata.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita consente di annullare la finestra cornice potrebbe essere in qualsiasi modalità di Guida. Eseguire l'override di questa funzione se si desidera eseguire un'elaborazione speciale quando la finestra cornice è attivata o disattivata.  
  
 Per ulteriori informazioni, vedere l'articolo [attivazione](../../mfc/activation-cpp.md)...  
  
##  <a name="ongetembeddeditem"></a>COleServerDoc:: OnGetEmbeddedItem  
 Chiamato dal framework quando un'applicazione contenitore chiama l'applicazione server per creare o modificare un elemento incorporato.  
  
```  
virtual COleServerItem* OnGetEmbeddedItem() = 0;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore a un elemento che rappresenta il documento. **NULL** se l'operazione non riuscita.  
  
### <a name="remarks"></a>Note  
 Non vi è nessuna implementazione predefinita. È necessario eseguire l'override di questa funzione per restituire un elemento che rappresenta l'intero documento. Il valore restituito deve essere un oggetto di un `COleServerItem`-classe derivata.  
  
##  <a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo  
 Il framework chiama questa funzione quando l'utente sceglie di annullare le modifiche apportate a un elemento che è stato attivato sul posto, modificato e successivamente disattivato.  
  
```  
virtual BOOL OnReactivateAndUndo();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita non esegue alcuna operazione tranne quella **FALSE** per indicare un errore.  
  
 Eseguire l'override di questa funzione se l'applicazione supporta l'annullamento. In genere è necessario eseguire l'operazione di annullamento, quindi attivare l'elemento chiamando `ActivateInPlace`. Se l'applicazione contenitore viene scritta con la libreria Microsoft Foundation Class, la chiamata `COleClientItem::ReactivateAndUndo` , questa funzione da chiamare.  
  
##  <a name="onresizeborder"></a>COleServerDoc::OnResizeBorder  
 Il framework chiama questa funzione quando ridimensionare finestre cornice dell'applicazione contenitore.  
  
```  
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,  
    LPOLEINPLACEUIWINDOW lpUIWindow,  
    BOOL bFrame);
```  
  
### <a name="parameters"></a>Parametri  
 `lpRectBorder`  
 Puntatore a un `RECT` struttura o un `CRect` oggetto che specifica le coordinate del bordo.  
  
 `lpUIWindow`  
 Puntatore a un oggetto della classe **IOleInPlaceUIWindow** che possiede la sessione di modifica sul posto.  
  
 *bFrame*  
 **TRUE** se `lpUIWindow` punta alla finestra cornice di primo livello dell'applicazione contenitore o **FALSE** se `lpUIWindow` punta a una finestra cornice di documento a livello dell'applicazione contenitore.  
  
### <a name="remarks"></a>Note  
 Questa funzione viene ridimensionata e regola le barre degli strumenti e altri elementi dell'interfaccia utente in base alle nuove dimensioni della finestra.  
  
 Per ulteriori informazioni, vedere [IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716) nel [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Questa è un' sottoponibile a override.  
  
##  <a name="onsethostnames"></a>COleServerDoc::OnSetHostNames  
 Chiamato dal framework quando il contenitore imposta o modifica i nomi host per questo documento.  
  
```  
virtual void OnSetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszHost`  
 Puntatore a una stringa che specifica il nome dell'applicazione contenitore.  
  
 `lpszHostObj`  
 Puntatore a una stringa che specifica il nome del contenitore per il documento.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita viene modificato il titolo del documento per tutte le visualizzazioni che fa riferimento a questo documento.  
  
 Eseguire l'override di questa funzione se l'applicazione imposta i titoli attraverso un meccanismo diverso.  
  
##  <a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects  
 Il framework chiama questa funzione per posizionare la finestra cornice modifica sul posto all'interno di una finestra cornice dell'applicazione contenitore.  
  
```  
virtual void OnSetItemRects(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parametri  
 `lpPosRect`  
 Puntatore a un `RECT` struttura o un `CRect` oggetto che specifica la posizione della finestra cornice sul posto rispetto all'area client dell'applicazione contenitore.  
  
 `lpClipRect`  
 Puntatore a un `RECT` struttura o un `CRect` oggetto che specifica il rettangolo di ridimensionamento della finestra cornice sul posto rispetto all'area client dell'applicazione contenitore.  
  
### <a name="remarks"></a>Note  
 Eseguire l'override di questa funzione per aggiornare il fattore di zoom della vista, se necessario.  
  
 Questa funzione viene in genere chiamata in risposta a un `RequestPositionChange` chiamare, anche se può essere chiamato in qualsiasi momento da contenitore per richiedere una modifica alla posizione per l'elemento sul posto.  
  
##  <a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars  
 Il framework chiama questa funzione per mostrare o nascondere le barre di controllo dell'applicazione server associate alla finestra cornice identificata da `pFrameWnd`.  
  
```  
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parametri  
 `pFrameWnd`  
 Puntatore alla finestra cornice con barre di controllo devono essere nascoste o visualizzate.  
  
 `bShow`  
 Determina se le barre di controllo vengono mostrate o nascoste.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita enumera tutte le barre di controllo appartenente a tale finestra cornice e consente di nascondere o Mostra loro.  
  
##  <a name="onshowdocument"></a>COleServerDoc::OnShowDocument  
 Il framework chiama la `OnShowDocument` funzione quando il documento server deve essere nascosto o visualizzato.  
  
```  
virtual void OnShowDocument(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametri  
 `bShow`  
 Specifica se l'interfaccia utente per il documento deve essere visualizzato o nascosto.  
  
### <a name="remarks"></a>Note  
 Se `bShow` è **TRUE**, l'implementazione predefinita attiva l'applicazione server, se necessario e fa sì che l'applicazione contenitore di scorrere la finestra in modo che l'elemento è visibile. Se `bShow` è **FALSE**, l'implementazione predefinita disattiva l'elemento tramite una chiamata a `OnDeactivate`, Elimina o nasconde tutte le finestre cornice create per il documento, ad eccezione del primo. Se non rimangono documenti visibili, l'implementazione predefinita nasconde l'applicazione server.  
  
##  <a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument  
 Chiamato dal framework quando il salvataggio di un documento che è un elemento incorporato in un documento composito.  
  
```  
virtual BOOL OnUpdateDocument();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se il documento è stato aggiornato correttamente; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 L'implementazione predefinita chiama la [COleServerDoc::NotifySaved](#notifysaved) e [COleServerDoc::SaveEmbedding](#saveembedding) membro le funzioni e quindi contrassegnato come di pulizia. Eseguire l'override di questa funzione se si desidera eseguire l'elaborazione durante l'aggiornamento di un elemento incorporato speciali.  
  
##  <a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange  
 Chiamare questa funzione membro per modificare la posizione dell'applicazione contenitore.  
  
```  
void RequestPositionChange(LPCRECT lpPosRect);
```  
  
### <a name="parameters"></a>Parametri  
 `lpPosRect`  
 Puntatore a un `RECT` struttura o un `CRect` oggetto che contiene la nuova posizione.  
  
### <a name="remarks"></a>Note  
 Questa funzione viene chiamata generalmente (insieme a `UpdateAllItems`) quando vengono modificati i dati in un elemento attivo sul posto. In seguito a questa chiamata, il contenitore potrebbe o la modifica potrebbe non funzionare chiamando `OnSetItemRects`. La posizione risulta potrebbe essere diversa da quello richiesto.  
  
##  <a name="saveembedding"></a>COleServerDoc::SaveEmbedding  
 Chiamare questa funzione per indicare l'applicazione contenitore per salvare l'oggetto incorporato.  
  
```  
void SaveEmbedding();
```  
  
### <a name="remarks"></a>Note  
 Questa funzione viene chiamata automaticamente da `OnUpdateDocument`. Si noti che questa funzione, l'elemento da aggiornare nel disco, in modo che in genere viene chiamato solo in seguito a un'azione dell'utente specifico.  
  
##  <a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy  
 Chiamare il `ScrollContainerBy` funzione membro per scorrere il documento contenitore, la quantità, in pixel, indicato da `sizeScroll`.  
  
```  
BOOL ScrollContainerBy(CSize sizeScroll);
```  
  
### <a name="parameters"></a>Parametri  
 `sizeScroll`  
 Indica la distanza scorrere il documento contenitore.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 I valori positivi indicano lo scorrimento verso il basso e verso destra. i valori negativi indicano lo scorrimento verticale e a sinistra.  
  
##  <a name="updateallitems"></a>COleServerDoc::UpdateAllItems  
 Chiamare questa funzione per notificare a tutti gli elementi collegati collegati al documento che è stato modificato il documento.  
  
```  
void UpdateAllItems(
    COleServerItem* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parametri  
 `pSender`  
 Puntatore all'elemento che il documento modificato o **NULL** se tutti gli elementi devono essere aggiornati.  
  
 `lHint`  
 Contiene informazioni sulla modifica.  
  
 `pHint`  
 Puntatore a un oggetto di archiviazione delle informazioni sulla modifica.  
  
 `nDrawAspect`  
 Determina il l'elemento da disegnare. Questo è un valore compreso il `DVASPECT` enumerazione. Per il parametro è possibile specificare uno dei valori riportati di seguito:  
  
- `DVASPECT_CONTENT`Elemento è rappresentato in modo tale che può essere visualizzata come un oggetto incorporato all'interno del relativo contenitore.  
  
- `DVASPECT_THUMBNAIL`Elemento viene eseguito il rendering in una rappresentazione "anteprima" in modo che possa essere visualizzata in uno strumento di esplorazione.  
  
- `DVASPECT_ICON`Elemento è rappresentato da un'icona.  
  
- `DVASPECT_DOCPRINT`Elemento è rappresentato come se fosse stampato utilizzando il comando Stampa dal menu File.  
  
### <a name="remarks"></a>Note  
 In genere si chiama questa funzione dopo che l'utente modifica il documento server. Se un elemento OLE è collegato al documento con un collegamento automatico, l'elemento viene aggiornato per riflettere le modifiche. Nelle applicazioni contenitore scritte con la libreria Microsoft Foundation Class di [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) funzione membro `COleClientItem` viene chiamato.  
  
 Questa funzione chiama la `OnUpdate` una funzione membro per tutti gli elementi del documento, ad eccezione dell'invio di elementi, passando `pHint`, `lHint`, e `nDrawAspect`. Utilizzare questi parametri per passare le informazioni per gli elementi sulle modifiche apportate al documento. È possibile codificare usando `lHint` oppure è possibile definire un `CObject`-derivata per memorizzare informazioni sulle modifiche e passare un oggetto di tale classe utilizzando `pHint`. Eseguire l'override di `OnUpdate` funzione membro nel `COleServerItem`-derivata per ottimizzare l'aggiornamento di ogni elemento a seconda se è stati modificati relativa presentazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio HIERSVR](../../visual-cpp-samples.md)   
 [Classe COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [COleDocument (classe)](../../mfc/reference/coledocument-class.md)   
 [Classe COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)   
 [Classe COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
