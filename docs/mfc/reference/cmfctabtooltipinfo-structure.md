---
title: Struttura CMFCTabToolTipInfo | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: 27
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
ms.openlocfilehash: b9750cd9369313a3ed6ea9474d401cd0068a75fa
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctabtooltipinfo-structure"></a>Struttura CMFCTabToolTipInfo
Questa struttura fornisce informazioni sulla scheda MDI che l'utente è posizionato il mouse.  
  
## <a name="syntax"></a>Sintassi  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## <a name="members"></a>Membri  
  
### <a name="data-members"></a>Membri di dati  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|Specifica l'indice del controllo scheda.|  
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|Puntatore al controllo struttura a schede.|  
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|Testo della descrizione comando.|  
  
## <a name="remarks"></a>Note  
 Un puntatore a un `CMFCTabToolTipInfo` struttura viene passata come parametro del `AFX_WM_ON_GET_TAB_TOOLTIP` messaggio. Questo messaggio viene generato quando vengono abilitate le schede MDI e il puntatore viene posizionato un controllo struttura a schede.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente viene illustrato come `CMFCTabToolTipInfo` viene utilizzata per la [esempio MDITabsDemo: applicazione MDI a schede MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo n.&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxbasetabctrl.h  
  
##  <a name="m_ntabindex"></a>CMFCTabToolTipInfo::m_nTabIndex  
 Specifica l'indice del controllo scheda.  
  
```  
int m_nTabIndex;  
```  
  
### <a name="remarks"></a>Note  
 Indice della scheda su cui si trova l'utente.  
  
### <a name="example"></a>Esempio  
 L'esempio seguente viene illustrato come `m_nTabIndex` viene utilizzata per la [esempio MDITabsDemo: applicazione MDI a schede MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo n.&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_ptabwnd"></a>CMFCTabToolTipInfo::m_pTabWnd  
 Puntatore al controllo struttura a schede.  
  
```  
CMFCBaseTabCtrl* m_pTabWnd;  
```  
  
### <a name="example"></a>Esempio  
 L'esempio seguente viene illustrato come `m_pTabWnd` viene utilizzata per la [esempio MDITabsDemo: applicazione MDI a schede MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo n.&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
##  <a name="m_strtext"></a>CMFCTabToolTipInfo::m_strText  
 Testo della descrizione comando.  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>Note  
 Se la stringa è vuota, la descrizione comandi non viene visualizzata.  
  
### <a name="example"></a>Esempio  
 L'esempio seguente viene illustrato come `m_strText` viene utilizzata per la [esempio MDITabsDemo: applicazione MDI a schede MFC](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo n.&2;](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)
