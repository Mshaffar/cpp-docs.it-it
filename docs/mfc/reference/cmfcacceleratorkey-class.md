---
title: Classe CMFCAcceleratorKey | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs: C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: "36"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3303be9f37749436d140028cd5fa45cd4454c8c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcacceleratorkey-class"></a>Classe CMFCAcceleratorKey
Classe helper che implementa virtuale mapping delle chiavi e la formattazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Costruisce un oggetto `CMFCAcceleratorKey`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|Converte la struttura di accelerazione per la rappresentazione visiva.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Imposta il tasto di scelta rapida per il `CMFCAcceleratorKey` oggetto.|  
  
## <a name="remarks"></a>Note  
 Tasti di scelta rapida sono noti anche come tasti di scelta rapida. Se si desidera visualizzare i tasti di scelta rapida che viene inserito un utente, il [classe CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapping dei tasti di scelta rapida, ad esempio Alt + Maiusc + S, in un formato di testo personalizzato, ad esempio "Alt + Maiusc + S". Ogni `CMFCAcceleratorKey` oggetto esegue il mapping di un tasto di scelta rapida singolo in un formato di testo.  
  
 Per ulteriori informazioni su come usare i tasti di scelta rapida e tasti di scelta rapida, vedere [CKeyboardManager classe](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato di seguito viene illustrato come costruire un `CMFCAcceleratorKey` oggetto e viene illustrato come utilizzare il relativo `Format` metodo.  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey  
 Costruisce un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) oggetto.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpAccel`  
 Puntatore a un tasto di scelta rapida.  
  
### <a name="remarks"></a>Note  
 Se un tasto di scelta rapida non fornire quando si crea un `CMFCAccleratorKey`, utilizzare il [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) metodo per associare un tasto di scelta rapida con il `CMFCAcceleratorKey` oggetto.  
  
##  <a name="format"></a>CMFCAcceleratorKey::Format  
 Converte la struttura di accelerazione per il valore di stringa associato.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [out] `str`  
 Un riferimento a un `CString` oggetto in cui il metodo scrive il tasto di scelta rapida tradotti.  
  
### <a name="remarks"></a>Note  
 Questo metodo recupera il formato di stringa del tasto di scelta rapida associato. È possibile impostare il formato della stringa di un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) oggetto utilizzando il costruttore o il metodo [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator  
 Imposta il tasto di scelta rapida per il [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) oggetto.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `lpAccel`  
 Puntatore a un tasto di scelta rapida.  
  
### <a name="remarks"></a>Note  
 Utilizzare questo metodo per impostare il tasto di scelta rapida per un `CMFCAcceleratorKey` se non si ha fornito un tasto di scelta rapida durante la creazione di `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)