---
title: Classe CMFCRibbonComboBox | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonComboBox class
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
caps.latest.revision: 35
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
ms.openlocfilehash: 747006ee66445eb312c22d658706e5fe81d2a958
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribboncombobox-class"></a>Classe CMFCRibbonComboBox
La `CMFCRibbonComboBox` classe implementa un controllo casella combinata che è possibile aggiungere una barra multifunzione, un pannello della barra multifunzione o un menu di scelta rapida della barra multifunzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## <a name="members"></a>Membri  
  
### <a name="constructors"></a>Costruttori  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Costruisce un oggetto CMFCRibbonComboBox.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](#additem)|Aggiunge un elemento univoco nella casella di riepilogo.|  
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Elimina un elemento specificato dalla casella di riepilogo.|  
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Specifica se la casella di riepilogo è possibile modificare le dimensioni trascinando verso il basso.|  
|[CMFCRibbonComboBox::FindItem](#finditem)|Restituisce l'indice del primo elemento nella casella di riepilogo che corrisponde a una stringa specificata.|  
|[CMFCRibbonComboBox::GetCount](#getcount)|Restituisce il numero di elementi nella casella di riepilogo.|  
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Ottiene l'indice dell'elemento attualmente selezionato nella casella di riepilogo.|  
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Ottiene l'altezza della casella di riepilogo quando la casella di riepilogo viene premuto.|  
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Restituisce le dimensioni della casella combinata come visualizzato in modalità intermedi.|  
|[CMFCRibbonComboBox::GetItem](#getitem)|Restituisce la stringa associata a un elemento in corrispondenza dell'indice specificato nella casella di riepilogo.|  
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Restituisce i dati associati a un elemento in corrispondenza dell'indice specificato nella casella di riepilogo.|  
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Indica se il controllo contiene una casella di modifica.|  
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Indica se è possibile ridimensionare la casella di riepilogo.|  
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Chiamato dal framework quando l'utente seleziona un elemento nella casella di riepilogo.|  
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Elimina tutti gli elementi dalla casella di riepilogo e deseleziona la casella di modifica.|  
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Seleziona un elemento nella casella di riepilogo.|  
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Imposta l'altezza della casella di riepilogo quando viene eliminato verso il basso.|  
  
## <a name="remarks"></a>Note  
 Casella combinata della barra multifunzione è costituito da una casella combinata con un'etichetta statica o etichetta che può essere modificato dall'utente. È necessario specificare il tipo desiderato quando si crea la casella combinata della barra multifunzione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come creare un oggetto della `CMFCRibbonComboBox` classe, aggiungere un elemento alla casella combinata, selezionare un elemento nella casella combinata e aggiungere una casella combinata a un pannello.  
  
 [!code-cpp[NVC_MFC_RibbonApp&#11;](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxribboncombobox.h  
  
##  <a name="additem"></a>CMFCRibbonComboBox::AddItem  
 Aggiunge un elemento univoco nella casella di riepilogo.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszItem`  
 La stringa dell'elemento da aggiungere.  
  
 [in] `dwData`  
 I dati associati all'elemento da aggiungere.  
  
### <a name="return-value"></a>Valore restituito  
 Indice in base zero dell'elemento aggiunto.  
  
##  <a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox  
 Costruisce un oggetto `CMFCRibbonComboBox`.  
  
```  
public:  
CMFCRibbonComboBox(
    UINT nID,  
    BOOL bHasEditBox=TRUE,  
    Int nWidth=-1,  
    LPCTSTR lpszLabel=NULL,  
    Int nImage=-1);

protected:  
CMFCRibbonComboBox();
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nID`  
 L'ID della casella combinata.  
  
 [in] `bHasEditBox`  
 `TRUE`Se si desidera che una casella di modifica nel controllo. `FALSE` in caso contrario.  
  
 [in] `nWidth`  
 Larghezza della casella combinata in pixel. oppure -1 per la larghezza predefinita.  
  
 [in] `lpszLabel`  
 Etichetta di visualizzazione della casella combinata.  
  
 [in] `nImage`  
 L'indice di immagine di ridotte dimensioni della casella combinata.  
  
### <a name="remarks"></a>Note  
 La larghezza predefinita è 108 pixel.  
  
##  <a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem  
 Elimina un elemento specificato dalla casella di riepilogo.  
  
```  
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `iIndex`  
 Indice in base zero dell'elemento da eliminare.  
  
 [in] `dwData`  
 I dati associati all'elemento da eliminare.  
  
 [in] `lpszText`  
 La stringa dell'elemento da eliminare. Se sono presenti più elementi con la stessa stringa, il primo elemento viene eliminato.  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se l'elemento specificato è stato eliminato; in caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Note  
  
##  <a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize  
 Specifica se la casella di riepilogo è possibile modificare le dimensioni trascinando verso il basso.  
  
```  
void EnableDropDownListResize(BOOL bEnable=FALSE);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `bEnable`  
 `TRUE`Per abilitare il ridimensionamento; `FALSE` per disabilitare il ridimensionamento.  
  
### <a name="remarks"></a>Note  
 Quando il ridimensionamento è abilitato, la casella di riepilogo viene modificato adatta gli elementi che vengono visualizzati.  
  
##  <a name="finditem"></a>CMFCRibbonComboBox::FindItem  
 Restituisce l'indice del primo elemento nella casella di riepilogo che corrisponde a una stringa specificata.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszText`  
 La stringa di un elemento nella casella di riepilogo.  
  
### <a name="return-value"></a>Valore restituito  
 L'indice in base zero dell'elemento; oppure -1 se l'elemento non viene trovato.  
  
### <a name="remarks"></a>Note  
  
##  <a name="getcount"></a>CMFCRibbonComboBox::GetCount  
 Restituisce il numero di elementi nella casella di riepilogo.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di elementi nella casella di riepilogo oppure 0 se la casella di riepilogo non contiene elementi.  
  
### <a name="remarks"></a>Note  
  
##  <a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel  
 Ottiene l'indice dell'elemento attualmente selezionato nella casella di riepilogo.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 L'indice in base zero dell'elemento attualmente selezionato nella casella di riepilogo. oppure -1 se è selezionato alcun elemento.  
  
##  <a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight  
 Ottiene l'altezza della casella di riepilogo quando la casella di riepilogo viene premuto.  
  
```  
int GetDropDownHeight();
```  
  
### <a name="return-value"></a>Valore restituito  
 L'altezza, in pixel, della casella di riepilogo.  
  
### <a name="remarks"></a>Note  
  
##  <a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize  
 Restituisce le dimensioni della casella combinata come visualizzato in modalità intermedi.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `pDC`  
 Puntatore a un contesto di dispositivo per la casella combinata.  
  
### <a name="return-value"></a>Valore restituito  
 Le dimensioni della casella combinata.  
  
### <a name="remarks"></a>Note  
 La dimensione restituita è basata sulle dimensioni della casella combinata durante la visualizzazione di immagini di piccole dimensioni.  
  
##  <a name="getitem"></a>CMFCRibbonComboBox::GetItem  
 Restituisce la stringa associata a un elemento in corrispondenza dell'indice specificato nella casella di riepilogo.  
  
```  
LPCTSTR GetItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [in] `iIndex`  
 Indice in base zero di un elemento nella casella di riepilogo.  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore a una stringa che è associato l'elemento. in caso contrario, `NULL` se il parametro di indice non è valido o se il parametro di indice è -1 e nessun elemento selezionato nella casella combinata.  
  
### <a name="remarks"></a>Note  
  
##  <a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData  
 Restituisce i dati associati a un elemento in corrispondenza dell'indice specificato nella casella di riepilogo.  
  
```  
DWORD_PTR GetItemData(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [in] `iIndex`  
 Indice in base zero di un elemento nella casella di riepilogo.  
  
### <a name="return-value"></a>Valore restituito  
 I dati associati all'elemento. oppure 0 se l'elemento non esiste o se il parametro di indice è -1 e non è selezionato alcun elemento nella casella di riepilogo.  
  
##  <a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox  
 Indica se il controllo contiene una casella di modifica.  
  
```  
BOOL HasEditBox() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se il controllo contiene una casella di modifica; in caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Note  
  
##  <a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList  
 Indica se è possibile ridimensionare la casella di riepilogo.  
  
```  
BOOL IsResizeDropDownList() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se la casella di riepilogo può essere ridimensionata; in caso contrario `FALSE`. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)  
  
### <a name="remarks"></a>Note  
 È possibile abilitare il ridimensionamento di casella elenco utilizzando il [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) metodo.  
  
##  <a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem  
 Chiamato dal framework quando un utente seleziona un elemento nella casella di riepilogo.  
  
```  
virtual void OnSelectItem(int nItem);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nItem`  
 L'indice dell'elemento selezionato.  
  
### <a name="remarks"></a>Note  
 Eseguire l'override di questo metodo se si desidera elaborare una selezione di input dell'utente.  
  
##  <a name="removeallitems"></a>CMFCRibbonComboBox::RemoveAllItems  
 Elimina tutti gli elementi dalla casella di riepilogo e deseleziona la casella di modifica.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Note  
  
##  <a name="selectitem"></a>CMFCRibbonComboBox::SelectItem  
 Seleziona un elemento nella casella di riepilogo.  
  
```  
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `iIndex`  
 Indice in base zero di un elemento nella casella di riepilogo.  
  
 [in] `dwData`  
 I dati associati a un elemento nella casella di riepilogo.  
  
 [in] `lpszText`  
 La stringa di un elemento nella casella di riepilogo.  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se il metodo ha esito positivo; in caso contrario `FALSE`.  
  
### <a name="remarks"></a>Note  
  
##  <a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight  
 Imposta l'altezza della casella di riepilogo quando viene eliminato verso il basso.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nHeight`  
 L'altezza, in pixel, della casella di riepilogo.  
  
### <a name="remarks"></a>Note  
 L'altezza predefinita è 150 pixel.  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)
