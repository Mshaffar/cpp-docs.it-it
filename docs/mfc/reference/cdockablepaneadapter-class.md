---
title: Classe CDockablePaneAdapter | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::GetWrappedWnd
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::LoadState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SaveState
- AFXDOCKABLEPANEADAPTER/CDockablePaneAdapter::SetWrappedWnd
dev_langs: C++
helpviewer_keywords:
- CDockablePaneAdapter [MFC], GetWrappedWnd
- CDockablePaneAdapter [MFC], LoadState
- CDockablePaneAdapter [MFC], SaveState
- CDockablePaneAdapter [MFC], SetWrappedWnd
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5bb0e10490a381784e40167e16d1c7ec4e7e1a19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="cdockablepaneadapter-class"></a>Classe CDockablePaneAdapter
Fornisce il supporto di ancoraggio per i riquadri derivati da `CWnd`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](#getwrappedwnd)|Restituisce la finestra di cui è stato eseguito il wrapping.|  
|[CDockablePaneAdapter::LoadState](#loadstate)|(Esegue l'override [CDockablePane:: LoadState](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917).)|  
|[CDockablePaneAdapter::SaveState](#savestate)|(Esegue l'override [CDockablePane:: SaveState](http://msdn.microsoft.com/en-us/c5c24249-8d0d-46cb-96d9-9f5c6dc191db).)|  
|[CDockablePaneAdapter::SetWrappedWnd](#setwrappedwnd)||  
  
## <a name="remarks"></a>Note  
 In genere, il framework crea istanze di oggetti di questa classe quando si utilizza il [cmfcbasetabctrl:: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) o [cmfcbasetabctrl:: insertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) metodi.  
  
 Se si desidera personalizzare il `CDockablePaneAdapter` comportamento, è sufficiente derivarne una nuova classe e impostare le informazioni sulla classe di runtime a una finestra a schede usando [:: Setdockingbarwrapperrtc](../../mfc/reference/cmfcbasetabctrl-class.md#setdockingbarwrapperrtc).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxdockablepaneadapter. H  
  
##  <a name="getwrappedwnd"></a>CDockablePaneAdapter::GetWrappedWnd  
 Restituisce la finestra sottostante per la scheda di un riquadro ancorabile.  
  
```  
virtual CWnd* GetWrappedWnd() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore alla finestra sottoposta a wrapping.  
  
### <a name="remarks"></a>Note  
 Utilizzare questa funzione per accedere alla finestra sottoposta a wrapping.  
  
##  <a name="loadstate"></a>CDockablePaneAdapter::LoadState  
 Carica lo stato del riquadro dal Registro di sistema.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszProfileName`  
 Nome del profilo.  
  
 [in] `nIndex`  
 L'indice di profilo.  
  
 [in] `uiID`  
 L'ID del riquadro.  
  
### <a name="return-value"></a>Valore restituito  
  
### <a name="remarks"></a>Note  
  
##  <a name="savestate"></a>CDockablePaneAdapter::SaveState  
 Salva lo stato del riquadro nel Registro di sistema.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpszProfileName`  
 Nome del profilo.  
  
 [in] `nIndex`  
 L'indice di profilo (impostazione predefinita l'ID di controllo della finestra).  
  
 [in] `uiID`  
 L'ID del riquadro.  
  
### <a name="return-value"></a>Valore restituito  
  
### <a name="remarks"></a>Note  
  
##  <a name="setwrappedwnd"></a>CDockablePaneAdapter::SetWrappedWnd  
 Imposta la finestra sottostante per la scheda di un riquadro ancorabile.  
  
```  
virtual BOOL SetWrappedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `pWnd`  
 Puntatore alla finestra per la scheda del riquadro eseguire il wrapping.  
  
### <a name="return-value"></a>Valore restituito  
  
### <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe CDockablePane](../../mfc/reference/cdockablepane-class.md)