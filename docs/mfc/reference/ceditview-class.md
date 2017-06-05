---
title: Classe CEditView | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
dev_langs:
- C++
helpviewer_keywords:
- text editors, CEditView class
- text editors
- edit controls, classes
- views, classes
- CEditView class
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
caps.latest.revision: 25
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
ms.openlocfilehash: 688a6c0e871a9456b85a8ed02ce43d7fa9ca8180
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="ceditview-class"></a>Classe CEditView
Tipo di classe di visualizzazione che fornisce la funzionalità di un controllo di modifica di Windows e che può essere utilizzato per implementare funzionalità di tipo editor di testo semplice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CEditView : public CCtrlView  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CEditView::CEditView](#ceditview)|Costruisce un oggetto di tipo `CEditView`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CEditView::FindText](#findtext)|Cerca una stringa all'interno del testo.|  
|[CEditView::GetBufferLength](#getbufferlength)|Ottiene la lunghezza del buffer di caratteri.|  
|[CEditView::GetEditCtrl](#geteditctrl)|Fornisce l'accesso per il `CEdit` parte di un `CEditView` oggetto (controllo di modifica di Windows).|  
|[CEditView::GetPrinterFont](#getprinterfont)|Recupera il carattere della stampante corrente.|  
|[CEditView::GetSelectedText](#getselectedtext)|Recupera la selezione di testo corrente.|  
|[CEditView::LockBuffer](#lockbuffer)|Blocca il buffer.|  
|[CEditView::PrintInsideRect](#printinsiderect)|Esegue il rendering di testo all'interno di un rettangolo specificato.|  
|[CEditView:: SerializeRaw](#serializeraw)|Serializza un `CEditView` oggetto su disco come testo non elaborato.|  
|[CEditView::SetPrinterFont](#setprinterfont)|Imposta un nuovo tipo di carattere della stampante.|  
|[CEditView::SetTabStops](#settabstops)|Imposta le tabulazioni per la visualizzazione su schermo e la stampa.|  
|[CEditView::UnlockBuffer](#unlockbuffer)|Sblocca il buffer.|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CEditView::OnFindNext](#onfindnext)|Cerca l'occorrenza successiva della stringa di testo.|  
|[CEditView::OnReplaceAll](#onreplaceall)|Sostituisce tutte le occorrenze di una stringa specificata con una nuova stringa.|  
|[CEditView::OnReplaceSel](#onreplacesel)|Sostituisce la selezione corrente.|  
|[CEditView::OnTextNotFound](#ontextnotfound)|Chiamato quando un'operazione di ricerca non riesce a trovare qualsiasi ulteriore testo.|  
  
### <a name="public-data-members"></a>Membri dati pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CEditView::dwStyleDefault](#dwstyledefault)|Stile predefinito per gli oggetti di tipo **CEditView.**|  
  
## <a name="remarks"></a>Note  
 La `CEditView` classe fornisce le funzioni aggiuntive seguenti:  
  
-   Stampa.  
  
-   Trova e sostituisci.  
  
 Poiché classe `CEditView` è un derivato di classe `CView`, gli oggetti della classe `CEditView` può essere utilizzato con documenti e modelli di documento.  
  
 Ogni `CEditView` testo del controllo viene mantenuto nell'oggetto memoria globale. L'applicazione può avere un numero qualsiasi di `CEditView` oggetti.  
  
 Creare gli oggetti di tipo `CEditView` se si desidera che una finestra di modifica con la funzionalità aggiunta elencata in precedenza o se si desidera aggiungere funzionalità di editor di testo semplice. Oggetto `CEditView` oggetto può occupare l'intera area client di una finestra. Derivare classi personalizzate da `CEditView` per aggiungere o modificare la funzionalità di base, o per dichiarare le classi che possono essere aggiunti a un modello di documento.  
  
 L'implementazione predefinita della classe `CEditView` gestisce i comandi seguenti: **ID_EDIT_SELECT_ALL**, **ID_EDIT_FIND**, **ID_EDIT_REPLACE**, **ID_EDIT_REPEAT**, e **ID_FILE_PRINT**.  
  
 Il limite di caratteri predefinito per `CEditView` è (1024 \* 1024-1 = 1048575). Questo comportamento può essere modificato chiamando il **EM_LIMITTEXT** controllo edit funzione dell'oggetto sottostante. Tuttavia, i limiti sono diversi a seconda del sistema operativo e il tipo di modifica controllo (singolo o multiriga). Per ulteriori informazioni su questi limiti, vedere [EM_LIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761607).  
  
 Per modificare questo limite nel controllo, eseguire l'override di `OnCreate()` funzione per la `CEditView` classe e inserire la riga di codice seguente:  
  
 [!code-cpp[NVC_MFCDocView&#65;](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]  
  
 Gli oggetti di tipo `CEditView` (o di tipi derivati da `CEditView`) presentano le limitazioni seguenti:  
  
- `CEditView`non implementa true ciò che viene visualizzato è il risultato di modifica (WYSIWYG). Dove è possibile scegliere tra la leggibilità sullo schermo e stampato corrispondente, `CEditView` opts per migliorare la leggibilità dello schermo.  
  
- `CEditView`possono visualizzare testo in un unico tipo di carattere. Non è supportata alcuna formattazione carattere speciale. Vedere la classe [CRichEditView](../../mfc/reference/cricheditview-class.md) per maggiore capacità.  
  
-   La quantità di testo un `CEditView` può contenere è limitato. I limiti sono identiche a quelle per il `CEdit` controllo.  
  
 Per ulteriori informazioni su `CEditView`, vedere [derivato Visualizzazione classi disponibili in MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CEditView`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** AFXEXT  
  
##  <a name="ceditview"></a>CEditView::CEditView  
 Costruisce un oggetto di tipo `CEditView`.  
  
```  
CEditView();
```  
  
### <a name="remarks"></a>Note  
 Dopo la costruzione dell'oggetto, è necessario chiamare il [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) funzione prima che venga utilizzato il controllo di modifica. Se si deriva una classe dalla classe `CEditView` e aggiungerlo al modello utilizzando `CWinApp::AddDocTemplate`, il framework chiama il costruttore di entrambi e **crea** (funzione).  
  
##  <a name="dwstyledefault"></a>CEditView::dwStyleDefault  
 Contiene lo stile predefinito del `CEditView` oggetto.  
  
```  
static const DWORD dwStyleDefault;  
```  
  
### <a name="remarks"></a>Note  
 Passare il membro statico come il `dwStyle` parametro il **crea** funzione per ottenere lo stile predefinito per il `CEditView` oggetto.  
  
##  <a name="findtext"></a>CEditView::FindText  
 Chiamare il `FindText` funzione per la ricerca di `CEditView` buffer di testo dell'oggetto.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bNext = TRUE,  
    BOOL bCase = TRUE);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszFind`  
 Il testo da trovare.  
  
 `bNext`  
 Specifica la direzione della ricerca. Se **TRUE**, la direzione di ricerca è verso la fine del buffer. Se **FALSE**, la direzione di ricerca è verso l'inizio del buffer.  
  
 `bCase`  
 Specifica se la ricerca viene fatta distinzione tra maiuscole e minuscole. Se **TRUE**, la ricerca viene fatta distinzione tra maiuscole e minuscole. Se **FALSE**, la ricerca non viene fatta distinzione tra maiuscole e minuscole.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se viene trovato il testo di ricerca; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 La funzione Cerca il testo nel buffer per il testo specificato da `lpszFind`, a partire dalla selezione corrente, nella direzione specificata da `bNext`e con distinzione maiuscole/minuscole specificato da `bCase`. Se il testo viene trovato, imposta la selezione per il testo trovato e restituisce un valore diverso da zero. Se il testo non viene trovato, la funzione restituisce 0.  
  
 In genere non è necessaria chiamare il `FindText` se si esegue l'override `OnFindNext`, che chiama `FindText`.  
  
##  <a name="getbufferlength"></a>CEditView::GetBufferLength  
 Chiamare questa funzione membro per ottenere il numero di caratteri attualmente nel buffer del controllo di modifica, escluso il carattere di terminazione null.  
  
```  
UINT GetBufferLength() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 La lunghezza della stringa nel buffer.  
  
##  <a name="geteditctrl"></a>CEditView::GetEditCtrl  
 Chiamare `GetEditCtrl` per ottenere un riferimento al controllo di modifica utilizzato per la visualizzazione di modifica.  
  
```  
CEdit& GetEditCtrl() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Riferimento a un oggetto `CEdit`.  
  
### <a name="remarks"></a>Note  
 Questo controllo è di tipo [CEdit](../../mfc/reference/cedit-class.md), pertanto è possibile modificare il controllo di modifica di Windows direttamente tramite il `CEdit` funzioni membro.  
  
> [!CAUTION]
>  Utilizzo di `CEdit` oggetto può modificare lo stato di Windows sottostante controllo edit. Ad esempio, è consigliabile non modificare le impostazioni di scheda utilizzando il [CEdit::SetTabStops](../../mfc/reference/cedit-class.md#settabstops) funzione perché `CEditView` memorizza nella cache queste impostazioni per l'utilizzo nel controllo di modifica e nella stampa. Utilizzare invece [CEditView::SetTabStops](#settabstops).  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCDocView&#66;](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]  
  
##  <a name="getprinterfont"></a>CEditView::GetPrinterFont  
 Chiamare `GetPrinterFont` per ottenere un puntatore a un [CFont](../../mfc/reference/cfont-class.md) oggetto che descrive il tipo di carattere della stampante corrente.  
  
```  
CFont* GetPrinterFont() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore a un `CFont` oggetto che specifica il carattere della stampante corrente; **NULL** se il tipo di carattere della stampante non è stata impostata. Il puntatore può essere temporaneo e non deve essere memorizzato per usi successivi.  
  
### <a name="remarks"></a>Note  
 Se il tipo di carattere della stampante non è stata impostata, l'impostazione predefinita il comportamento di stampa di `CEditView` è classe stampa con lo stesso carattere utilizzato per la visualizzazione.  
  
 Utilizzare questa funzione per determinare il tipo di carattere della stampante corrente. Se non è il tipo di carattere della stampante desiderata, utilizzare [CEditView::SetPrinterFont](#setprinterfont) per modificarlo.  
  
##  <a name="getselectedtext"></a>CEditView::GetSelectedText  
 Chiamare `GetSelectedText` per copiare il testo selezionato in un `CString` oggetto, fino alla fine della selezione o il carattere che precede il primo carattere di ritorno a capo nella selezione.  
  
```  
void GetSelectedText(CString& strResult) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `strResult`  
 Un riferimento di `CString` oggetto che riceverà il testo selezionato.  
  
##  <a name="lockbuffer"></a>CEditView::LockBuffer  
 Chiamare questa funzione membro per ottenere un puntatore al buffer. Il buffer non deve essere modificato.  
  
```  
LPCTSTR LockBuffer() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore al buffer del controllo di modifica.  
  
##  <a name="onfindnext"></a>CEditView::OnFindNext  
 Cerca il testo nel buffer per il testo specificato da `lpszFind`, nella direzione specificata da `bNext`, con distinzione maiuscole/minuscole specificato da `bCase`.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszFind`  
 Il testo da trovare.  
  
 `bNext`  
 Specifica la direzione della ricerca. Se **TRUE**, la direzione di ricerca è verso la fine del buffer. Se **FALSE**, la direzione di ricerca è verso l'inizio del buffer.  
  
 `bCase`  
 Specifica se la ricerca viene fatta distinzione tra maiuscole e minuscole. Se **TRUE**, la ricerca viene fatta distinzione tra maiuscole e minuscole. Se **FALSE**, la ricerca non viene fatta distinzione tra maiuscole e minuscole.  
  
### <a name="remarks"></a>Note  
 La ricerca inizia all'inizio della selezione corrente e viene eseguita tramite una chiamata a [FindText](#findtext). Nell'implementazione predefinita `OnFindNext` chiamate [OnTextNotFound](#ontextnotfound) se non viene trovato il testo.  
  
 Eseguire l'override `OnFindNext` per modificare il modo in cui un `CEditView`-oggetto derivato da ricerca di testo. `CEditView`chiamate `OnFindNext` quando l'utente sceglie il pulsante Trova successivo nella finestra di dialogo Trova standard.  
  
##  <a name="onreplaceall"></a>CEditView::OnReplaceAll  
 `CEditView`chiamate `OnReplaceAll` quando l'utente seleziona il pulsante Sostituisci tutto nella finestra di dialogo Sostituisci standard.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszFind`  
 Il testo da trovare.  
  
 `lpszReplace`  
 Il testo per sostituire il testo di ricerca.  
  
 `bCase`  
 Specifica se ricerca viene fatta distinzione tra maiuscole e minuscole. Se **TRUE**, la ricerca viene fatta distinzione tra maiuscole e minuscole. Se **FALSE**, la ricerca non viene fatta distinzione tra maiuscole e minuscole.  
  
### <a name="remarks"></a>Note  
 `OnReplaceAll`Cerca il testo nel buffer per il testo specificato da `lpszFind`, con distinzione maiuscole/minuscole specificato da `bCase`. La ricerca inizia all'inizio della selezione corrente. Ogni volta che il testo di ricerca viene trovato, questa funzione sostituisce l'occorrenza del testo con il testo specificato da `lpszReplace`. La ricerca viene eseguita tramite una chiamata a [FindText](#findtext). Nell'implementazione predefinita [OnTextNotFound](#ontextnotfound) viene chiamato se il testo non viene trovato.  
  
 Se la selezione corrente non corrisponde a `lpszFind`, la selezione viene aggiornata per la prima occorrenza del testo specificato da `lpszFind` e non viene eseguita una sostituzione. Ciò consente all'utente di verificare che sia che si desidera eseguire quando la selezione non corrisponde a testo da sostituire.  
  
 Eseguire l'override `OnReplaceAll` per modificare il modo in cui un `CEditView`-oggetto derivato sostituisce il testo.  
  
##  <a name="onreplacesel"></a>CEditView::OnReplaceSel  
 `CEditView`chiamate `OnReplaceSel` quando l'utente seleziona il pulsante Sostituisci nella finestra di dialogo Sostituisci standard.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszFind`  
 Il testo da trovare.  
  
 `bNext`  
 Specifica la direzione della ricerca. Se **TRUE**, la direzione di ricerca è verso la fine del buffer. Se **FALSE**, la direzione di ricerca è verso l'inizio del buffer.  
  
 `bCase`  
 Specifica se la ricerca viene fatta distinzione tra maiuscole e minuscole. Se **TRUE**, la ricerca viene fatta distinzione tra maiuscole e minuscole. Se **FALSE**, la ricerca non viene fatta distinzione tra maiuscole e minuscole.  
  
 `lpszReplace`  
 Testo da sostituire il testo trovato.  
  
### <a name="remarks"></a>Note  
 Dopo aver sostituito la selezione, la funzione Cerca il testo nel buffer per l'occorrenza successiva del testo specificato da `lpszFind`, nella direzione specificata da `bNext`, con distinzione maiuscole/minuscole specificato da `bCase`. La ricerca viene eseguita tramite una chiamata a [FindText](#findtext). Se il testo non viene trovato, [OnTextNotFound](#ontextnotfound) viene chiamato.  
  
 Eseguire l'override `OnReplaceSel` per modificare il modo in cui un `CEditView`-oggetto derivato sostituisce il testo selezionato.  
  
##  <a name="ontextnotfound"></a>CEditView::OnTextNotFound  
 Eseguire l'override di questa funzione per modificare l'implementazione predefinita che chiama la funzione Windows **MessageBeep**.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszFind`  
 Il testo da trovare.  
  
##  <a name="printinsiderect"></a>CEditView::PrintInsideRect  
 Chiamare `PrintInsideRect` stampa di testo nel rettangolo specificato da *rectLayout*.  
  
```  
UINT PrintInsideRect(
    CDC *pDC,  
    RECT& rectLayout,  
    UINT nIndexStart,  
    UINT nIndexStop);
```  
  
### <a name="parameters"></a>Parametri  
 `pDC`  
 Puntatore al contesto di dispositivo stampante.  
  
 *rectLayout*  
 Fare riferimento a un [CRect](../../atl-mfc-shared/reference/crect-class.md) oggetto o [struttura RECT](../../mfc/reference/rect-structure1.md) che specifica il rettangolo in cui il testo viene eseguito il rendering.  
  
 `nIndexStart`  
 Indice all'interno del buffer del primo carattere deve essere eseguito il rendering.  
  
 `nIndexStop`  
 Indice all'interno del buffer del carattere che segue l'ultimo carattere da sottoporre a rendering.  
  
### <a name="return-value"></a>Valore restituito  
 L'indice del carattere successivo per la stampa (vale a dire il carattere che segue l'ultimo carattere viene eseguito il rendering).  
  
### <a name="remarks"></a>Note  
 Se il `CEditView` controllo non è applicato lo stile **ES_AUTOHSCROLL**, viene eseguito il wrapping di testo all'interno del rettangolo di rendering. Se il controllo è applicato lo stile **ES_AUTOHSCROLL**, il testo viene troncato a destra del rettangolo.  
  
 Il **rect.bottom** elemento il *rectLayout* oggetto viene modificato in modo che le dimensioni del rettangolo definiscono la parte del rettangolo originale che è occupato dal testo.  
  
##  <a name="serializeraw"></a>CEditView:: SerializeRaw  
 Chiamare `SerializeRaw` avere un `CArchive` lettura dell'oggetto o il testo scritto `CEditView` oggetto in un file di testo.  
  
```  
void SerializeRaw(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametri  
 `ar`  
 Riferimento per il `CArchive` oggetto che archivia il testo serializzato.  
  
### <a name="remarks"></a>Note  
 `SerializeRaw`è diverso da `CEditView`dell'implementazione interna del `Serialize` , che legge e scrive solo il testo, senza dati descrizione dell'oggetto.  
  
##  <a name="setprinterfont"></a>CEditView::SetPrinterFont  
 Chiamare `SetPrinterFont` per impostare il tipo di carattere della stampante per il tipo di carattere specificato da `pFont`.  
  
```  
void SetPrinterFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parametri  
 `pFont`  
 Un puntatore a un oggetto di tipo `CFont`. Se **NULL**, il tipo di carattere utilizzato per la stampa è basato sul tipo di carattere visualizzazione.  
  
### <a name="remarks"></a>Note  
 Se si desidera che la visualizzazione di utilizzare sempre un particolare tipo di carattere per la stampa, includere una chiamata a `SetPrinterFont` nella propria classe `OnPreparePrinting` (funzione). Questa funzione viene chiamata prima della stampa, quindi la modifica del tipo di carattere non viene effettuata prima della stampa di contenuto della visualizzazione.  
  
##  <a name="settabstops"></a>CEditView::SetTabStops  
 Chiamare questa funzione per impostare i punti di tabulazione utilizzati per la visualizzazione e stampa.  
  
```  
void SetTabStops(int nTabStops);
```  
  
### <a name="parameters"></a>Parametri  
 `nTabStops`  
 Larghezza di ogni tabulazione, in unità di finestra di dialogo.  
  
### <a name="remarks"></a>Note  
 È supportata solo una singola larghezza tabulazione. ( `CEdit` oggetti supportano più larghezza delle schede.) Larghezze si trovano in unità di finestra di dialogo, che è uguale a un quarto della larghezza del carattere medio (in caratteri maiuscoli e minuscoli alfabetici solo basata) del tipo di carattere utilizzato al momento della stampa o la visualizzazione. È consigliabile non utilizzare `CEdit::SetTabStops` poiché `CEditView` deve memorizzare nella cache il valore di tabulazione.  
  
 Questa funzione consente di modificare solo le schede dell'oggetto per cui è definito. Per modificare la scheda tabulazioni per ogni `CEditView` oggetto nell'applicazione, chiamare ogni oggetto `SetTabStops` (funzione).  
  
### <a name="example"></a>Esempio  
 Questo frammento di codice imposta le tabulazioni nel controllo a ogni quarto carattere misurando attentamente il tipo di carattere che viene utilizzato il controllo.  
  
 [!code-cpp[NVC_MFCDocView&#67;](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]  
  
##  <a name="unlockbuffer"></a>CEditView::UnlockBuffer  
 Chiamare questa funzione membro per sbloccare il buffer.  
  
```  
void UnlockBuffer() const;  
```  
  
### <a name="remarks"></a>Note  
 Chiamare `UnlockBuffer` dopo aver terminato di utilizzare il puntatore restituito da [LockBuffer](#lockbuffer).  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio MFC SUPERPAD](../../visual-cpp-samples.md)   
 [Classe CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classe CEdit](../../mfc/reference/cedit-class.md)   
 [CDocument (classe)](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)   
 [Classe CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [CRichEditView (classe)](../../mfc/reference/cricheditview-class.md)
