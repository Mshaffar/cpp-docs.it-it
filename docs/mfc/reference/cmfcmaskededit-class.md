---
title: Classe CMFCMaskedEdit | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
dev_langs:
- C++
helpviewer_keywords:
- CMFCMaskedEdit class
- CMFCMaskedEdit constructor
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
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
ms.openlocfilehash: 174551ecd75df8691d2a6086cbc074516f6d2045
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmaskededit-class"></a>Classe CMFCMaskedEdit
La `CMFCMaskedEdit` classe supporta un controllo di modifica mascherato, che convalida l'input dell'utente rispetto a una maschera e visualizza i risultati convalidati in base a un modello.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCMaskedEdit : public CEdit  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`CMFCMaskedEdit::CMFCMaskedEdit`|Costruttore predefinito.|  
|`CMFCMaskedEdit::~CMFCMaskedEdit`|Distruttore.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCMaskedEdit::DisableMask](#disablemask)|Disabilita la convalida dell'input dell'utente.|  
|[CMFCMaskedEdit::EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|Specifica se il `GetWindowText` che consente di recuperare solo i caratteri mascherati.|  
|[CMFCMaskedEdit::EnableMask](#enablemask)|Controllo di modifica consente di inizializzare il mascherata.|  
|[CMFCMaskedEdit::EnableSelectByGroup](#enableselectbygroup)|Specifica se il controllo di modifica mascherato seleziona determinati gruppi di input dell'utente o input dell'utente.|  
|[CMFCMaskedEdit::EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|Specifica se il testo viene convalidato solo mascherato caratteri o in base alla maschera intera.|  
|`CMFCMaskedEdit::GetThisClass`|Utilizzato dal framework per ottenere un puntatore al [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) oggetto associato a questo tipo di classe.|  
|[CMFCMaskedEdit::GetWindowText](#getwindowtext)|Recupera convalidati dal controllo MaskedEdit.|  
|[CMFCMaskedEdit::SetValidChars](#setvalidchars)|Specifica una stringa di caratteri validi che l'utente può immettere.|  
|[CMFCMaskedEdit::SetWindowText](#setwindowtext)|Visualizza un messaggio nel controllo di modifica mascherato.|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCMaskedEdit::IsMaskedChar](#ismaskedchar)|Chiamato dal framework per convalidare il carattere specificato con il carattere corrispondente.|  
  
## <a name="remarks"></a>Note  
 Eseguire i passaggi seguenti per utilizzare il `CMFCMaskedEdit` controllo nell'applicazione:  
  
 1. Incorporare un `CMFCMaskedEdit` oggetto nella classe di finestra.  
  
 2. Chiamare il [CMFCMaskedEdit::EnableMask](#enablemask) per specificare la maschera.  
  
 3. Chiamare il [CMFCMaskedEdit::SetValidChars](#setvalidchars) per specificare l'elenco di caratteri validi.  
  
 4. Chiamare il [CMFCMaskedEdit::SetWindowText](#setwindowtext) per specificare il testo predefinito per il controllo MaskedEdit.  
  
 5. Chiamare il [CMFCMaskedEdit::GetWindowText](#getwindowtext) metodo per recuperare il testo convalidato.  
  
 Se non si chiama uno o più metodi per inizializzare la maschera di caratteri validi e testo predefinito, il controllo MaskedEdit si comporta esattamente come si comporta il controllo di modifica standard.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come impostare la maschera (ad esempio un numero di telefono) utilizzando il `EnableMask` metodo per creare la maschera per il controllo MaskedEdit, il `SetValidChars` per specificare una stringa di caratteri validi che l'utente può immettere, e `SetWindowText` metodo per visualizzare un prompt dei comandi in mascherata il controllo di modifica. Questo esempio fa parte di [esempio nuovi controlli](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls&#11;](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls&#12;](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 [CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxmaskededit.h  
  
##  <a name="disablemask"></a>CMFCMaskedEdit::DisableMask  
 Disabilita la convalida dell'input dell'utente.  
  
```  
void DisableMask();
```  
  
### <a name="remarks"></a>Note  
 Se la convalida dell'input utente è disabilitato, il controllo MaskedEdit si comporta come controllo di modifica standard.  
  
##  <a name="enablegetmaskedcharsonly"></a>CMFCMaskedEdit::EnableGetMaskedCharsOnly  
 Specifica se il `GetWindowText` che consente di recuperare solo i caratteri mascherati.  
  
```  
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `bEnable`  
 `TRUE`Per specificare che il [CMFCMaskedEdit::GetWindowText](#getwindowtext) metodo recuperare mascherato solo caratteri. `FALSE` per specificare che il metodo di recuperare l'intero testo. Il valore predefinito è `TRUE`.  
  
### <a name="remarks"></a>Note  
 Utilizzare questo metodo per consentire il recupero di caratteri mascherati. Creare quindi un controllo di modifica mascherato che corrisponde al numero di telefono, ad esempio (425) 555-0187. Se si chiama il `GetWindowText` (metodo), restituisce "4255550187". Se si disabilita il recupero di caratteri mascherati, il `GetWindowText` metodo restituisce il testo che viene visualizzato nel controllo di modifica, ad esempio "(425) 555-0187".  
  
##  <a name="enablemask"></a>CMFCMaskedEdit::EnableMask  
 Controllo di modifica consente di inizializzare il mascherata.  
  
```  
void EnableMask(
    LPCTSTR lpszMask,  
    LPCTSTR lpszInputTemplate,  
    TCHAR chMaskInputTemplate=_T('_'),  
    LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszMask`  
 Una stringa della maschera che specifica il tipo di carattere che può essere visualizzati in ogni posizione di input dell'utente. La lunghezza del `lpszInputTemplate` e `lpszMask` le stringhe di parametri devono essere uguale. Vedere la sezione Osservazioni per ulteriori informazioni sui caratteri della maschera.  
  
 [in] `lpszInputTemplate`  
 Una stringa di modello maschera che specifica che il valore letterale di caratteri che può essere visualizzati in ogni posizione di input dell'utente. Utilizzare il carattere di sottolineatura ('_') come segnaposto carattere. La lunghezza del `lpszInputTemplate` e `lpszMask` le stringhe di parametri devono essere uguale.  
  
 [in] `chMaskInputTemplate`  
 Un carattere che sostituisce il framework per ogni carattere non valido nell'input dell'utente. Il valore predefinito di questo parametro è un carattere di sottolineatura ('_').  
  
 [in] `lpszValid`  
 Stringa che contiene un set di caratteri validi. `NULL`indica che tutti i caratteri sono validi. Il valore predefinito di questo parametro è `NULL`.  
  
### <a name="remarks"></a>Note  
 Utilizzare questo metodo per creare la maschera per il controllo di modifica mascherato. Derivare una classe dal `CMFCMaskedEdit` classe ed eseguire l'override di [CMFCMaskedEdit::IsMaskedChar](#ismaskedchar) metodo da utilizzare il proprio codice per l'elaborazione di maschera personalizzata.  
  
 Nella tabella seguente elenca i caratteri di maschera predefinito:  
  
|Carattere maschera|Definizione|  
|--------------------|----------------|  
|D|Cifra.|  
|g|Numero o spazio.|  
|+|Più (+) ('+ '), meno ('-'), o uno spazio.|  
|C|Carattere alfabetico.|  
|c|Carattere alfabetico o uno spazio.|  
|A|Carattere alfanumerico.|  
|a|Carattere alfanumerico o spazio.|  
|*|Un carattere stampabile.|  
  
##  <a name="enableselectbygroup"></a>CMFCMaskedEdit::EnableSelectByGroup  
 Specifica se il controllo MaskedEdit consente all'utente di selezionare determinati gruppi input o di tutti gli input.  
  
```  
void EnableSelectByGroup(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `bEnable`  
 `TRUE`Per selezionare solo i gruppi; `FALSE` per selezionare l'intero testo. Il valore predefinito è `TRUE`.  
  
### <a name="remarks"></a>Note  
 Utilizzare questa funzione per specificare se il controllo MaskedEdit consente all'utente di selezionare per gruppo o l'intero testo.  
  
 Per impostazione predefinita, la selezione dal gruppo è abilitata. In questo caso l'utente può selezionare solo continua gruppi di caratteri validi.  
  
 Ad esempio, utilizzare il controllo di modifica mascherato seguente per convalidare un numero di telefono:  
  
 `m_wndMaskEdit.EnableMask(`  
  
 `_T(" ddd  ddd dddd"),// Mask string`  
  
 `_T("(___) ___-____"),// Template string`  
  
 `_T(' '));// Default char`  
  
 `m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.`  
  
 `m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt`  
  
 Se è attivata la selezione dal gruppo, l'utente può recuperare solo il "425", "555" o "0187" gruppi di stringa. Se la selezione del gruppo è disabilitata l'utente può recuperare l'intero testo del numero di telefono: "(425) 555-0187".  
  
##  <a name="enablesetmaskedcharsonly"></a>CMFCMaskedEdit::EnableSetMaskedCharsOnly  
 Specifica se il testo viene convalidato solo i caratteri mascherati, o in base alla maschera intera.  
  
```  
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `bEnable`  
 `TRUE`per convalidare l'utente input rispetto a mascherato solo caratteri. `FALSE` per convalidare l'intera maschera. Il valore predefinito è `TRUE`.  
  
##  <a name="getwindowtext"></a>CMFCMaskedEdit::GetWindowText  
 Recupera convalidati dal controllo MaskedEdit.  
  
```  
int GetWindowText(
    LPTSTR lpszStringBuf,  
    int nMaxCount) const;  
  
void GetWindowText(CString& rstrString) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [out] `lpszStringBuf`  
 Un puntatore a un buffer che riceve il testo dal controllo di modifica.  
  
 [in] `nMaxCount`  
 Numero massimo di caratteri da ricevere.  
  
 [out] `rstrString`  
 Un riferimento all'oggetto stringa che riceve il testo dal controllo di modifica.  
  
### <a name="return-value"></a>Valore restituito  
 Il primo overload del metodo restituisce il numero di byte della stringa che viene copiato il `lpszStringBuf` buffer del parametro; 0 se il controllo di modifica mascherato non dispone di alcun testo.  
  
### <a name="remarks"></a>Note  
 Questo metodo copia il testo del controllo di modifica mascherato dal `lpszStringBuf` buffer o `rstrString` stringa.  
  
 Questo metodo consente di ridefinire [CWnd::GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext).  
  
##  <a name="ismaskedchar"></a>CMFCMaskedEdit::IsMaskedChar  
 Chiamato dal framework per convalidare il carattere specificato con il carattere corrispondente.  
  
```  
virtual BOOL IsMaskedChar(
    TCHAR chChar,  
    TCHAR chMaskChar) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [in] `chChar`  
 Carattere da convalidare.  
  
 [in] `chMaskChar`  
 Il carattere corrispondente dalla stringa di filtro.  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se il `chChar` parametro è il tipo di carattere consentito dal `chMaskChar` parametro; in caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Note  
 Eseguire l'override di questo metodo per convalidare i caratteri di input per conto proprio. Per ulteriori informazioni sui caratteri maschera, vedere il [CMFCMaskedEdit::EnableMask](#enablemask) metodo.  
  
##  <a name="setvalidchars"></a>CMFCMaskedEdit::SetValidChars  
 Specifica una stringa di caratteri validi che l'utente può immettere.  
  
```  
void SetValidChars(LPCTSTR lpszValid=NULL);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszValid`  
 Stringa che contiene il set di caratteri di input validi. `NULL`significa che tutti i caratteri sono validi. Il valore predefinito di questo parametro è `NULL`.  
  
### <a name="remarks"></a>Note  
 Utilizzare questo metodo per definire un elenco di caratteri validi. Se un carattere di input non è presente nell'elenco, controllo di modifica mascherato non lo accetta.  
  
 Nell'esempio seguente accetta solo numeri esadecimali.  
  
 `//Mask: 0xFFFFm_wndMaskEdit.EnableMask( _T(" AAAA"),                // The mask string. _T("0x____"),               // The literal template string. _T('_'));                   // The default character that replaces the backspace character.// Valid string charactersm_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));`  
  
##  <a name="setwindowtext"></a>CMFCMaskedEdit::SetWindowText  
 Visualizza un messaggio nel controllo di modifica mascherato.  
  
```  
void SetWindowText(LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszString`  
 Punta a una stringa con terminazione null che verrà utilizzato come un prompt dei comandi.  
  
### <a name="remarks"></a>Note  
 Questo metodo imposta il testo del controllo.  
  
 Questo metodo consente di ridefinire [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe CEdit](../../mfc/reference/cedit-class.md)
