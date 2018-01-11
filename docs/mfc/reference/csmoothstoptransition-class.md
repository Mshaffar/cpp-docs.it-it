---
title: Classe CSmoothStopTransition | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
dev_langs: C++
helpviewer_keywords:
- CSmoothStopTransition [MFC], CSmoothStopTransition
- CSmoothStopTransition [MFC], Create
- CSmoothStopTransition [MFC], m_dblFinalValue
- CSmoothStopTransition [MFC], m_maximumDuration
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50753ab65b960ac590c3f859133adf9da903aeda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="csmoothstoptransition-class"></a>Classe CSmoothStopTransition
Incapsula una transizione a interruzione graduale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CSmoothStopTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|Costruisce una transizione a interruzione graduale e inizializza la durata massima e il valore finale.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CSmoothStopTransition::Create](#create)|Chiama la libreria di transizione per creare oggetti COM di transizione incapsulato. (Esegue l'override [CBaseTransition:: Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Membri dati pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|Il valore della variabile di animazione alla fine della transizione.|  
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|La durata massima della transizione.|  
  
## <a name="remarks"></a>Note  
 Una transizione a interruzione graduale rallenta così come si avvicina a un determinato valore finale e raggiunge con una velocità uguale a zero. La durata della transizione è determinata dalla velocità iniziale, la differenza tra i valori iniziali e finali e la durata massima specificata. Se non esiste alcuna soluzione composta da un singolo arco parabolico, questo metodo crea una transizione cubica. Poiché tutte le transizioni vengono cancellate automaticamente, è consigliabile per assegnarle utilizzando l'operatore new. L'oggetto COM IUIAnimationTransition incapsulato viene creato da CAnimationController:: AnimateGroup, finché non è NULL. Modifica le variabili membro dopo la creazione dell'oggetto COM non ha alcun effetto.  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxanimationcontroller.h  
  
##  <a name="create"></a>CSmoothStopTransition::Create  
 Chiama la libreria di transizione per creare oggetti COM di transizione incapsulato.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametri  
 `pLibrary`  
 Puntatore alla raccolta di transizione, che è responsabile della creazione di transizioni standard.  
  
### <a name="return-value"></a>Valore restituito  
 TRUE se transizione viene creata correttamente. in caso contrario FALSE.  
  
##  <a name="csmoothstoptransition"></a>CSmoothStopTransition::CSmoothStopTransition  
 Costruisce una transizione a interruzione graduale e inizializza la durata massima e il valore finale.  
  
```  
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parametri  
 `maximumDuration`  
 La durata massima della transizione.  
  
 `dblFinalValue`  
 Il valore della variabile di animazione alla fine della transizione.  
  
##  <a name="m_dblfinalvalue"></a>CSmoothStopTransition::m_dblFinalValue  
 Il valore della variabile di animazione alla fine della transizione.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_maximumduration"></a>CSmoothStopTransition::m_maximumDuration  
 La durata massima della transizione.  
  
```  
UI_ANIMATION_SECONDS m_maximumDuration;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Classi](../../mfc/reference/mfc-classes.md)