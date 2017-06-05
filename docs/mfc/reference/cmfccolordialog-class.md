---
title: Classe CMFCColorDialog | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorDialog::m_CurrentColor data member
- CMFCColorDialog::m_pPropSheet data member
- CMFCColorDialog::m_btnColorSelect data member
- CMFCColorDialog class
- CMFCColorDialog::m_wndColors data member
- CMFCColorDialog::m_bIsMyPalette data member
- CMFCColorDialog::m_pColourSheetTwo data member
- CMFCColorDialog::m_NewColor data member
- CMFCColorDialog::m_pPalette data member
- CMFCColorDialog::m_wndStaticPlaceHolder data member
- CMFCColorDialog::m_pColourSheetOne data member
- CMFCColorDialog::m_hcurPicker data member
- CMFCColorDialog::PreTranslateMessage method
- CMFCColorDialog::m_bPickerMode data member
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 30
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
ms.openlocfilehash: ac621157e0fcb5bcabef2ae8f367a1b141b4ace0
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccolordialog-class"></a>Classe CMFCColorDialog
La `CMFCColorDialog` classe rappresenta una finestra di dialogo Selezione colori.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Costruisce un oggetto `CMFCColorDialog`.|  
|`CMFCColorDialog::~CMFCColorDialog`|Distruttore.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|Restituisce il colore selezionato corrente.|  
|[CMFCColorDialog::GetPalette](#getpalette)|Restituisce una tavolozza di colori.|  
|`CMFCColorDialog::PreTranslateMessage`|Converte i messaggi della finestra prima che vengano inviati per il [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) e [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funzioni di Windows. Per la sintassi e altre informazioni, vedere [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). Esegue l'override di `CDialogEx::PreTranslateMessage`.|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Deriva una tavolozza dalla tavolozza di sistema.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Imposta il colore selezionato corrente.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Imposta il colore più simile a un valore RGB specificato.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Seleziona un valore RGB per la prima pagina di proprietà.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Seleziona un valore RGB per la seconda pagina di proprietà.|  
  
### <a name="protected-data-members"></a>Membri dati protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE`Se la finestra di dialogo di selezione colore utilizza una proprio tavolozza dei colori o `FALSE` se la finestra di dialogo viene utilizzata una tavolozza specificata nella `CMFCColorDialog` costruttore.|  
|`m_bPickerMode`|`TRUE`mentre l'utente seleziona un colore dalla finestra di dialogo Selezione; in caso contrario, `FALSE`.|  
|`m_btnColorSelect`|Pulsante colore che l'utente ha selezionato.|  
|`m_CurrentColor`|Il colore selezionato.|  
|`m_hcurPicker`|Il cursore utilizzato per selezionare un colore.|  
|`m_NewColor`|Il potenziale colore selezionato, che può essere selezionato o ripristinare il colore originale in modo permanente.|  
|`m_pColourSheetOne`|Puntatore alla prima pagina delle proprietà della finestra delle proprietà di selezione colore.|  
|`m_pColourSheetTwo`|Puntatore alla seconda pagina delle proprietà della finestra delle proprietà di selezione colore.|  
|`m_pPalette`|La tavolozza logica corrente.|  
|`m_pPropSheet`|Puntatore alla finestra delle proprietà per la finestra di dialogo di selezione colore.|  
|`m_wndColors`|Un oggetto di controllo di selezione colore.|  
|`m_wndStaticPlaceHolder`|Un controllo statico è un segnaposto per la finestra delle proprietà di selezione colore.|  
  
## <a name="remarks"></a>Note  
 La finestra di dialogo Selezione colori viene visualizzata come una finestra delle proprietà con due pagine. La prima pagina selezionare un colore standard dalla tavolozza di sistema; Nella seconda pagina, si seleziona un colore personalizzato.  
  
 È possibile costruire un `CMFCColorDialog` nello stack e quindi chiamare `DoModal`, passando il colore iniziale come parametro per il `CMFCColorDialog` costruttore. La finestra di dialogo Selezione colori, quindi crea più [CMFCColorPickerCtrl classe](../../mfc/reference/cmfccolorpickerctrl-class.md) oggetti per gestire ogni tavolozza dei colori.  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come configurare una finestra di dialogo colore tramite i vari metodi di `CMFCColorDialog` (classe). Nell'esempio viene illustrato come impostare l'oggetto corrente e i nuovi colori della finestra di dialogo e come impostare i componenti rosso, verdi e blu del colore selezionato nella pagina delle due proprietà della finestra di dialogo colore. Questo esempio fa parte di [esempio nuovi controlli](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls n.&3;](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog  
 Costruisce un oggetto `CMFCColorDialog`.  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `clrInit`  
 La selezione di colori predefinita. Se viene specificato alcun valore, il valore predefinito è RGB(0,0,0) (nero).  
  
 [in] `dwFlags`  
 (Riservato).  
  
 [in] `pParentWnd`  
 Puntatore alla finestra padre o proprietaria della finestra di dialogo.  
  
 [in] `hPal`  
 Handle per una tavolozza dei colori.  
  
### <a name="return-value"></a>Valore restituito  
  
### <a name="remarks"></a>Note  
  
##  <a name="getcolor"></a>CMFCColorDialog::GetColor  
 Recupera il colore selezionato dall'utente nella finestra di dialogo colore.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) contenente le informazioni per il colore selezionato nella finestra di dialogo colore RGB.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata di `DoModal` metodo.  
  
##  <a name="getpalette"></a>CMFCColorDialog::GetPalette  
 Recupera la tavolozza dei colori disponibili nella finestra di dialogo colore corrente.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore per il `CPalette` oggetto specificato nel `CMFCColorDialog` costruttore.  
  
### <a name="remarks"></a>Note  
 La tavolozza dei colori specifica i colori che l'utente può scegliere.  
  
##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette  
 Deriva una tavolozza dalla tavolozza di sistema.  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor  
 Imposta il colore corrente nella finestra di dialogo.  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `rgb`  
 Un valore di colore RGB  
  
### <a name="remarks"></a>Note  
  
##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor  
 Imposta il colore corrente per il colore della tavolozza corrente che è molto simile.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `rgb`  
 Oggetto [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) che specifica un colore RGB.  
  
### <a name="remarks"></a>Note  
  
##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne  
 Specifica in modo esplicito i componenti rosso, verdi e blu del colore selezionato nella pagina delle proprietà prima di una finestra di dialogo colore.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `R`  
 Specifica il componente rosso del valore RGB.  
  
 [in] `G`  
 Specifica il componente verde del valore RGB.  
  
 [in] `B`  
 Specifica il componente blu del valore RGB.  
  
### <a name="remarks"></a>Note  
  
##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo  
 Specifica in modo esplicito i componenti rosso, verdi e blu del colore selezionato nella seconda pagina delle proprietà di una finestra di dialogo colore.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `R`  
 Specifica un componente rosso del valore RGB  
  
 [in] `G`  
 Specifica un componente di un valore RGB verde  
  
 [in] `B`  
 Specifica un componente blu di un valore RGB  
  
### <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe di CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
