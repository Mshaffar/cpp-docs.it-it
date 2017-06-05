---
title: Classe CMFCRibbonStatusBarPane | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane class
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: 31
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
ms.openlocfilehash: a101e50f55efab44e4cb66d314b2426228dbc5c0
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonstatusbarpane-class"></a>Classe CMFCRibbonStatusBarPane
La `CMFCRibbonStatusBarPane` classe implementa un elemento della barra multifunzione che è possibile aggiungere a una barra di stato multifunzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Costruisce e inizializza un oggetto `CMFCRibbonStatusBarPane`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Restituisce la stringa che definisce la stringa di testo più lunga che può essere visualizzata nel riquadro senza troncamenti.|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Restituisce l'impostazione corrente di allineamento del testo.|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Determina se l'animazione è in corso.|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Determina se il riquadro situato nell'area estesa della barra di stato della barra multifunzione.|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Esegue l'override di [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Esegue l'override di [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Definisce la stringa di testo più lunga che può essere visualizzata nel riquadro senza troncamenti.|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Assegna al riquadro di un elenco di immagini che può essere utilizzato per l'animazione.|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Imposta l'allineamento del testo.|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Avvia l'animazione che viene assegnato al riquadro.|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Arresta l'animazione che viene assegnato al riquadro. .|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Chiamato dal framework quando si arresta l'animazione che viene assegnato al riquadro.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come usare vari metodi nella classe `CMFCRibbonStatusBarPane`. Nell'esempio viene illustrato come costruire un `CMFCRibbonStatusBarPane` di oggetto, impostare l'allineamento del testo dell'etichetta del riquadro della barra di stato, definire il testo più lungo che possono essere visualizzati nel riquadro della barra di stato senza troncamento, collegare al riquadro della barra di stato di un elenco di immagini che può essere utilizzato per l'animazione e avvia l'animazione.  
  
 [!code-cpp[NVC_MFC_RibbonApp n.&2;](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 Costruire un oggetto di riquadro nella barra di stato.  
  
```  
CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    BOOL bIsStatic=FALSE,  
    HICON hIcon=NULL,  
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nCmdID`  
 Specifica l'ID di comando del riquadro.  
  
 [in] `lpszText`  
 Specifica la stringa di testo da visualizzare nel riquadro.  
  
 [in] `bIsStatic`  
 Se `TRUE`, nel riquadro di stato non può essere evidenziato o selezionato facendovi clic sopra.  
  
 [in] `hIcon`  
 Specifica un handle per un'icona da visualizzare nel riquadro.  
  
 [in] `lpszAlmostLargeText`  
 Specifica la stringa di testo più lunga che può essere visualizzata nel riquadro.  
  
 [in] `hBmpAnimationList`  
 Specifica un handle per un elenco di immagini che viene utilizzato per l'animazione.  
  
 [in] `cxAnimation`  
 Specifica la larghezza, in pixel, dell'icona nell'elenco di immagini che viene utilizzato per l'animazione.  
  
 [in] `clrTrnsp`  
 Specifica il colore trasparente delle immagini nell'elenco di immagini che vengono utilizzati per l'animazione.  
  
 [in] `uiAnimationListResID`  
 Specifica un ID di risorsa di un elenco di immagini che viene utilizzato per l'animazione.  
  
##  <a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText  
 Ottiene la stringa di testo più lunga in grado di visualizzare il riquadro della barra di stato.  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 La stringa di testo più lunga in grado di visualizzare il riquadro della barra di stato.  
  
##  <a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign  
 Ottiene l'impostazione corrente dell'allineamento del testo dell'etichetta del riquadro della barra di stato.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 L'allineamento del testo corrente che può essere uno dei seguenti:  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT.  
  
##  <a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation  
 Determina se l'animazione è in corso.  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se l'animazione è in corso. `FALSE` in caso contrario.  
  
##  <a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended  
 Determinare se il riquadro situato nell'area estesa della barra di stato della barra multifunzione.  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se il riquadro è area estesa della barra di stato. In caso contrario, `FALSE`.  
  
##  <a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `CDC*`  
  
### <a name="remarks"></a>Note  
  
##  <a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `pDC`  
  
### <a name="return-value"></a>Valore restituito  
  
### <a name="remarks"></a>Note  
  
##  <a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation  
 Framework chiama questo metodo quando termina l'animazione che viene assegnato al riquadro.  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>Note  
 `StopAnimation`chiamate al metodo di `OnFinishAnimation` metodo, che è possibile utilizzare per pulire i dati quando l'animazione viene terminata.  
  
##  <a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText  
 Definire il testo più lungo che può essere visualizzato nel riquadro della barra di stato senza troncamenti.  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszAlmostLargeText`  
 Specifica la stringa più lunga che può essere visualizzata nel riquadro della barra di stato senza troncamenti.  
  
### <a name="remarks"></a>Note  
 La libreria calcola le dimensioni del testo che `lpszAlmostLargeText` specifica e ridimensiona il riquadro di conseguenza. Il testo verrà troncato se ancora non rientra nel riquadro.  
  
##  <a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList  
 Si collega al riquadro della barra di stato per un elenco di immagini che può essere utilizzato per l'animazione.  
  
```  
void SetAnimationList(
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `hBmpAnimationList`  
 Specifica un handle per un elenco di immagini.  
  
 [in] `cxAnimation`  
 Specifica la larghezza, in pixel, del frame dell'elenco immagini.  
  
 [in] `clrTransp`  
 Specifica il colore trasparente dell'elenco immagini.  
  
 [in] `uiAnimationListResID`  
 Specifica l'ID risorsa dell'elenco immagini.  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se l'elenco di immagini sia stato collegato correttamente per il riquadro barra di stato. `FALSE` in caso contrario.  
  
##  <a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign  
 Imposta l'allineamento del testo dell'etichetta del riquadro della barra di stato.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nAlign`  
 Specifica l'allineamento del testo.  
  
### <a name="remarks"></a>Note  
 `nAlign`può avere uno dei valori seguenti:  
  
- `TA_LEFT`: l'allineamento a sinistra  
  
- `TA_CENTER:`Allinea al centro  
  
- `TA_RIGHT:`allineamento a destra  
  
##  <a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation  
 Avvia l'animazione che si assegna al riquadro.  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nFrameDelay`  
 Specifica la frequenza dei fotogrammi di animazione, in millisecondi.  
  
 [in] `nDuration`  
 Specifica il tempo di riproduzione dell'animazione, in millisecondi. Utilizzare -1 per un ciclo infinito.  
  
### <a name="remarks"></a>Note  
 È necessario specificare un handle per un elenco di immagini prima di chiamare `StartAnimation` utilizzando `SetAnimationList`.  
  
##  <a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation  
 Arresta l'animazione assegnata al riquadro della barra di stato.  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Classe CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)
