---
title: Mappe Sink di evento | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- event sink maps
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
caps.latest.revision: 14
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
ms.sourcegitcommit: 17a158366f94d27b7a46917282425d652e6b9042
ms.openlocfilehash: 33bf66d18b499787a34b2da501bb3e8ead255459
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="event-sink-maps"></a>Mappe sink di evento
Quando un controllo OLE incorporato viene generato un evento, il contenitore riceve l'evento mediante un meccanismo, definito "evento sink mappa" fornita da MFC. Questa mappa del sink di evento consente di definire le funzioni del gestore per ogni evento specifico, nonché i parametri di tali eventi. Per ulteriori informazioni sulle mappe sink di evento, vedere l'articolo [contenitori dei controlli ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="event-sink-maps"></a>Mappe sink di evento  
  
|||  
|-|-|  
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Inizia la definizione di una mappa del sink di evento.|  
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Dichiara una mappa del sink di evento.|  
|[END_EVENTSINK_MAP](#end_eventsink_map)|Termina la definizione di una mappa del sink di evento.|  
|[ON_EVENT](#on_event)|Definisce un gestore eventi per un evento specifico.|  
|[ON_EVENT_RANGE](#on_event_range)|Definisce un gestore eventi per un evento specifico generato da un set di controlli OLE.|  
|[ON_EVENT_REFLECT](#on_event_reflect)|Riceve gli eventi generati dal controllo prima che vengano gestiti dal contenitore del controllo.|  
|[ON_PROPNOTIFY](#on_propnotify)|Definisce un gestore per la gestione delle notifiche di proprietà da un controllo OLE.|  
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definisce un gestore per la gestione delle notifiche di proprietà da un set di controlli OLE.|  
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Riceve le notifiche di proprietà inviate dal controllo prima vengono gestiti dal contenitore del controllo.|  
  
##  <a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP  
 Inizia la definizione della mappa del sink di evento.  
  
```   
BEGIN_EVENTSINK_MAP(theClass, baseClass)  
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 Specifica il nome della classe del controllo mappa la cui sink di evento.  
  
 `baseClass`  
 Specifica il nome della classe base di `theClass`.  
  
### <a name="remarks"></a>Note  
 Nel file di implementazione (. cpp) che definisce le funzioni membro per la classe, avviare la mappa di sink di evento con il `BEGIN_EVENTSINK_MAP` (macro), quindi aggiungere le voci di macro per ogni evento ricevere una notifica di e completare la mappa del sink di evento con il `END_EVENTSINK_MAP` (macro).  
  
 Per informazioni sulle mappe sink di evento e i contenitori di controlli OLE, vedere l'articolo [contenitori dei controlli ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP  
 Un contenitore OLE può fornire una mappa del sink di evento per specificare gli eventi che verrà notificato nel contenitore.  
  
```   
DECLARE_EVENTSINK_MAP()   
```  
  
### <a name="remarks"></a>Note  
 Utilizzare il `DECLARE_EVENTSINK_MAP` (macro) alla fine della dichiarazione di classe. Quindi, nel. Le funzioni file CPP che definisce il membro della classe, utilizzare il `BEGIN_EVENTSINK_MAP` (macro), le voci di macro per ognuno degli eventi per ricevere una notifica e `END_EVENTSINK_MAP` macro per dichiarare la fine dell'elenco di sink di eventi.  
  
 Per ulteriori informazioni sulle mappe sink di evento, vedere l'articolo [contenitori dei controlli ActiveX](../../mfc/activex-control-containers.md).  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** AFXWIN. h  
  
##  <a name="end_eventsink_map"></a>END_EVENTSINK_MAP  
 Termina la definizione della mappa del sink di evento.  
  
```   
END_EVENTSINK_MAP()   
```  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="on_event"></a>ON_EVENT  
 Utilizzare il `ON_EVENT` macro per definire una funzione del gestore eventi per un evento generato da un controllo OLE.  
  
```   
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 La classe a cui appartiene questa mappa del sink di evento.  
  
 `id`  
 L'ID di controllo del controllo OLE.  
  
 `dispid`  
 L'ID di invio dell'evento generato dal controllo.  
  
 `pfnHandler`  
 Puntatore a una funzione membro che gestisce l'evento. Questa funzione deve avere un **BOOL** il tipo restituito e tipi di parametro che corrispondono ai parametri dell'evento (vedere `vtsParams`). La funzione deve restituire **TRUE** per indicare l'evento è stato gestito; in caso contrario **FALSE**.  
  
 `vtsParams`  
 Una sequenza di **VTS _** costanti che specifica i tipi dei parametri per l'evento. Queste sono le costanti stesse che vengono utilizzate nelle voci della mappa di invio come `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Note  
 Il `vtsParams` argomento è un elenco di valori separati da spazi di **VTS _** costanti. Uno o più di questi valori separati da spazi (non virgole) specifica l'elenco dei parametri della funzione. Ad esempio:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Specifica un elenco contenente un valore short integer seguito da un **BOOL**.  
  
 Per un elenco di **VTS _** costanti, vedere [EVENT_CUSTOM](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="on_event_range"></a>ON_EVENT_RANGE  
 Utilizzare il `ON_EVENT_RANGE` macro per definire una funzione del gestore eventi per un evento attivato da qualsiasi controllo OLE con un ID di controllo all'interno di un intervallo contiguo di ID.  
  
```   
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)   
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 La classe a cui appartiene questa mappa del sink di evento.  
  
 `idFirst`  
 L'ID di controllo del primo controllo OLE nell'intervallo.  
  
 `idLast`  
 L'ID di controllo dell'ultimo controllo OLE nell'intervallo.  
  
 `dispid`  
 L'ID di invio dell'evento generato dal controllo.  
  
 `pfnHandler`  
 Puntatore a una funzione membro che gestisce l'evento. Questa funzione deve avere un **BOOL** il tipo restituito, un primo parametro di tipo **UINT** (per l'ID di controllo) e tipi di parametri aggiuntivi che corrispondono ai parametri dell'evento (vedere `vtsParams`). La funzione deve restituire **TRUE** per indicare l'evento è stato gestito; in caso contrario **FALSE**.  
  
 `vtsParams`  
 Una sequenza di **VTS _** costanti che specifica i tipi dei parametri per l'evento. La prima costante deve essere di tipo **VTS_I4**, per l'ID di controllo. Queste sono le costanti stesse che vengono utilizzate nelle voci della mappa di invio come `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Note  
 Il `vtsParams` argomento è un elenco di valori separati da spazi di **VTS _** costanti. Uno o più di questi valori separati da spazi (non virgole) specifica l'elenco dei parametri della funzione. Ad esempio:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Specifica un elenco contenente un valore short integer seguito da un **BOOL**.  
  
 Per un elenco di **VTS _** costanti, vedere [EVENT_CUSTOM](event-maps.md#event_custom).  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un gestore eventi, per l'evento MouseDown, implementato per tre controlli ( `IDC_MYCTRL1` tramite `IDC_MYCTRL3`). Funzione del gestore eventi `OnRangeMouseDown`, viene dichiarata nel file di intestazione della classe di finestra ( `CMyDlg`) come:  
  
 [!code-cpp[NVC_MFCAutomation&#12;](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]  
  
 Il codice seguente viene definito nel file di implementazione della classe di finestra di dialogo.  
  
 [!code-cpp[13 NVC_MFCAutomation](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="on_event_reflect"></a>ON_EVENT_REFLECT  
 Il `ON_EVENT_REFLECT` (macro), quando utilizzato nell'evento mappa sink della classe wrapper del controllo OLE, riceve gli eventi generati dal controllo prima che vengano gestiti dal contenitore del controllo.  
  
```   
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams) 
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 La classe a cui appartiene questa mappa del sink di evento.  
  
 DISPID  
 L'ID di invio dell'evento generato dal controllo.  
  
 `pfnHandler`  
 Puntatore a una funzione membro che gestisce l'evento. Questa funzione deve avere un **BOOL** il tipo restituito e i tipi di parametro che corrispondono ai parametri dell'evento (vedere `vtsParams`). La funzione deve restituire **TRUE** per indicare l'evento è stato gestito; in caso contrario **FALSE**.  
  
 `vtsParams`  
 Una sequenza di **VTS _** costanti che specifica i tipi dei parametri per l'evento. Queste sono le costanti stesse che vengono utilizzate nelle voci della mappa di invio come `DISP_FUNCTION`.  
  
### <a name="remarks"></a>Note  
 Il `vtsParams` argomento è un elenco di valori separati da spazi di **VTS _** costanti.  
  
 Uno o più di questi valori separati da spazi (non virgole) specifica l'elenco dei parametri della funzione. Ad esempio:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Specifica un elenco contenente un valore short integer seguito da un **BOOL**.  
  
 Per un elenco di **VTS _** costanti, vedere [EVENT_CUSTOM](event-maps.md#event_custom).  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="on_propnotify"></a>ON_PROPNOTIFY  
 Utilizzare il `ON_PROPNOTIFY` macro per definire una voce di mappa eventi sink per la gestione delle notifiche di proprietà da un controllo OLE.  
  
```   
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 La classe a cui appartiene questa mappa del sink di evento.  
  
 `id`  
 L'ID di controllo del controllo OLE.  
  
 `dispid`  
 ID dispatch della proprietà di notifica.  
  
 `pfnRequest`  
 Puntatore a una funzione membro che gestisce il **OnRequestEdit** notifica per questa proprietà. Questa funzione deve avere un **BOOL** tipo restituito e un **BOOL\* ** parametro. Questa funzione deve impostare il parametro **TRUE** per consentire la proprietà da modificare e **FALSE** non è consentita. La funzione deve restituire **TRUE** per indicare la notifica è stata gestita; in caso contrario **FALSE**.  
  
 `pfnChanged`  
 Puntatore a una funzione membro che gestisce il **OnChanged** notifica per questa proprietà. La funzione deve avere un **BOOL** tipo restituito e un **UINT** parametro. La funzione deve restituire **TRUE** per indicare che la notifica è stato gestito; in caso contrario **FALSE**.  
  
### <a name="remarks"></a>Note  
 Il `vtsParams` argomento è un elenco di valori separati da spazi di **VTS _** costanti. Uno o più di questi valori separati da spazi (non virgole) specifica l'elenco dei parametri della funzione. Ad esempio:  
  
 [!code-cpp[NVC_MFCAutomation&#11;](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]  
  
 Specifica un elenco contenente un valore short integer seguito da un **BOOL**.  
  
 Per un elenco di **VTS _** costanti, vedere [EVENT_CUSTOM](event-maps.md#event_custom).  
  
##  <a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE  
 Utilizzare il `ON_PROPNOTIFY_RANGE` macro per definire una voce di mapping di sink di evento per la gestione delle notifiche di proprietà da qualsiasi controllo OLE con un ID di controllo all'interno di un intervallo contiguo di ID.  
  
```  
 
ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 La classe a cui appartiene questa mappa del sink di evento.  
  
 `idFirst`  
 L'ID di controllo del primo controllo OLE nell'intervallo.  
  
 `idLast`  
 L'ID di controllo dell'ultimo controllo OLE nell'intervallo.  
  
 `dispid`  
 ID dispatch della proprietà di notifica.  
  
 `pfnRequest`  
 Puntatore a una funzione membro che gestisce il **OnRequestEdit** notifica per questa proprietà. Questa funzione deve avere un **BOOL** tipo restituito e **UINT** e **BOOL\* ** parametri. La funzione deve impostare il parametro **TRUE** per consentire la proprietà da modificare e **FALSE** non è consentita. La funzione deve restituire **TRUE** per indicare che la notifica è stato gestito; in caso contrario **FALSE**.  
  
 `pfnChanged`  
 Puntatore a una funzione membro che gestisce il **OnChanged** notifica per questa proprietà. La funzione deve avere un **BOOL** tipo restituito e un **UINT** parametro. La funzione deve restituire **TRUE** per indicare che la notifica è stato gestito; in caso contrario **FALSE**.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT  
 Il `ON_PROPNOTIFY_REFLECT` (macro), quando utilizzato nell'evento mappa sink della classe wrapper del controllo OLE, riceve le notifiche di proprietà inviate dal controllo prima vengono gestiti dal contenitore del controllo.  
  
```  
 
ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)  
 
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 La classe a cui appartiene questa mappa del sink di evento.  
  
 `dispid`  
 ID dispatch della proprietà di notifica.  
  
 `pfnRequest`  
 Puntatore a una funzione membro che gestisce il **OnRequestEdit** notifica per questa proprietà. Questa funzione deve avere un **BOOL** tipo restituito e un **BOOL\* ** parametro. Questa funzione deve impostare il parametro **TRUE** per consentire la proprietà da modificare e **FALSE** non è consentita. La funzione deve restituire **TRUE** per indicare la notifica è stata gestita; in caso contrario **FALSE**.  
  
 `pfnChanged`  
 Puntatore a una funzione membro che gestisce il **OnChanged** notifica per questa proprietà. La funzione deve avere un **BOOL** il tipo restituito e senza parametri. La funzione deve restituire **TRUE** per indicare la notifica è stata gestita; in caso contrario **FALSE**.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
    
## <a name="see-also"></a>Vedere anche  
 [Macro e funzioni globali](../../mfc/reference/mfc-macros-and-globals.md)
