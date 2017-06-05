---
title: Mappe di connessione | Documenti di Microsoft
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
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: 12
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
ms.openlocfilehash: 8947930d20cc65075abe442b233e4c086f10f76e
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="connection-maps"></a>Mappe di connessione
OLE (controlli) sono in grado di esporre interfacce ad altre applicazioni. Queste interfacce consentono solo l'accesso da un contenitore in tale controllo. Se un controllo OLE esigenza di accedere alle interfacce esterne di altri oggetti OLE, è necessario stabilire un punto di connessione. Questo punto di connessione consente a un controllo in uscita di accesso alle mappe di invio esterne, ad esempio mappe eventi o le funzioni di notifica.  
  
 La libreria Microsoft Foundation Class offre un modello di programmazione che supporta i punti di connessione. In questo modello, "connessione mappe" vengono utilizzati per definire le interfacce o dei punti di connessione per il controllo OLE. Mappe di connessione contengono una macro per ogni punto di connessione. Per ulteriori informazioni sulle mappe di connessione, vedere il [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) (classe).  
  
 In genere, un controllo supporterà solo da due punti di connessione: uno per gli eventi e uno per le notifiche di proprietà. Questi vengono implementati dalla `COleControl` classe di base e richiedono un lavoro aggiuntivo dal writer del controllo. I punti di connessione aggiuntive che si desidera implementare nella classe devono essere aggiunti manualmente. Per supportare le mappe di connessione e i punti, MFC fornisce le seguenti macro:  
  
### <a name="connection-map-declaration-and-demarcation"></a>Connessione mappa dichiarazione e delimitazione della  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Dichiara una classe incorporata che implementa un punto di connessione aggiuntive (deve essere utilizzato nella dichiarazione di classe).|  
|[END_CONNECTION_PART](#end_connection_part)|Termina la dichiarazione di un punto di connessione (deve essere utilizzato nella dichiarazione di classe).|  
|[CONNECTION_IID](#connection_iid)|Specifica l'ID di interfaccia del controllo punto di connessione.|  
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Dichiara una mappa di connessioni verrà utilizzata in una classe (deve essere utilizzato nella dichiarazione di classe).|  
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Inizia la definizione di una mappa di connessioni (deve essere utilizzata nell'implementazione della classe).|  
|[END_CONNECTION_MAP](#end_connection_map)|Termina la definizione di una mappa di connessioni (deve essere utilizzata nell'implementazione della classe).|  
|[CONNECTION_PART](#connection_part)|Specifica un punto di connessione nella mappa delle connessioni del controllo.|  
  
 Le funzioni seguenti facilitare un sink di stabilire e disconnessione di una connessione utilizzando i punti di connessione:  
  
### <a name="initializationtermination-of-connection-points"></a>Inizializzazione/terminazione dei punti di connessione  
  
|||  
|-|-|  
|[AfxConnectionAdvise](#afxconnectionadvise)|Stabilisce una connessione tra un'origine e sink.|  
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Interrompe una connessione tra un'origine e sink.|  
  
##  <a name="begin_connection_part"></a>BEGIN_CONNECTION_PART  
 Utilizzare il `BEGIN_CONNECTION_PART` macro per iniziare la definizione dei punti di connessione aggiuntive oltre i punti di connessione di notifica eventi e proprietà.  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 Specifica il nome della classe del controllo la cui connessione faccia questo.  
  
 *localClass*  
 Specifica il nome della classe locale che implementa il punto di connessione.  
  
### <a name="remarks"></a>Note  
 Nel file di dichiarazione (h) che definisce le funzioni membro per la classe, avviare il punto di connessione con il `BEGIN_CONNECTION_PART` (macro), quindi aggiungere il `CONNECTION_IID` macro e altre funzioni membro che si desidera implementare e completare la mappa dei punti di connessione con il `END_CONNECTION_PART` (macro).  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="end_connection_part"></a>END_CONNECTION_PART  
 Termina la dichiarazione del punto di connessione.  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>Parametri  
 *localClass*  
 Specifica il nome della classe locale che implementa il punto di connessione.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="connection_iid"></a>CONNECTION_IID  
 Utilizzare tra il `BEGIN_CONNECTION_PART` e `END_CONNECTION_PART` macro per definire un ID di interfaccia per un punto di connessione supportato dal controllo OLE.  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>Parametri  
 `iid`  
 L'ID di interfaccia dell'interfaccia denominata dal punto di connessione.  
  
### <a name="remarks"></a>Note  
 Il `iid` argomento è un'interfaccia ID utilizzato per identificare l'interfaccia che il punto di connessione verrà chiamata relativi sink connesso. Ad esempio:  
  
 [!code-cpp[NVC_MFCConnectionPoints&#10;](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 Specifica un punto di connessione che chiama il `ISinkInterface` interfaccia.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="declare_connection_map"></a>DECLARE_CONNECTION_MAP  
 Ogni `COleControl`-classe derivata nel programma può fornire una mappa di connessione per specificare i punti di connessione aggiuntive che supporta il controllo.  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>Note  
 Se il controllo supporta punti aggiuntivi, utilizzare il `DECLARE_CONNECTION_MAP` (macro) alla fine della dichiarazione di classe. Quindi, nel file cpp che definisce le funzioni membro per la classe, utilizzare il `BEGIN_CONNECTION_MAP` (macro), `CONNECTION_PART` macro per ognuno dei punti di connessione del controllo e `END_CONNECTION_MAP` macro per dichiarare la fine della mappa di connessione.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="begin_connection_map"></a>BEGIN_CONNECTION_MAP  
 Ogni classe derivata da `COleControl` nel programma può fornire una mappa di connessioni per specificare i punti di connessione che il controllo supporterà.  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 Specifica il nome della classe del controllo a cui appartiene la mappa delle connessioni.  
  
 *theBase*  
 Specifica il nome della classe base di `theClass`.  
  
### <a name="remarks"></a>Note  
 Nell'implementazione (. File CPP) che definisce le funzioni membro per la classe, avviare la mappa delle connessioni con il `BEGIN_CONNECTION_MAP` (macro), quindi aggiungere le voci di macro per ognuno dei punti di connessione utilizzando il [CONNECTION_PART](#connection_part) (macro). Infine, completare la mappa delle connessioni con il [END_CONNECTION_MAP](#end_connection_map) (macro).  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="end_connection_map"></a>END_CONNECTION_MAP  
 Termina la definizione della mappa delle connessioni.  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="connection_part"></a>CONNECTION_PART  
 Esegue il mapping di un punto di connessione per il controllo OLE a un ID di interfaccia specifica.  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>Parametri  
 `theClass`  
 Specifica il nome della classe del controllo la cui connessione faccia questo.  
  
 `iid`  
 L'ID di interfaccia dell'interfaccia denominata dal punto di connessione.  
  
 *localClass*  
 Specifica il nome della classe locale che implementa il punto di connessione.  
  
### <a name="remarks"></a>Note  
 Ad esempio:  
  
 [!code-cpp[NVC_MFCConnectionPoints n.&2;](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 implementa una mappa delle connessioni, con un punto di connessione, che chiama il `IID_ISinkInterface` interfaccia.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxdisp. h  
  
##  <a name="afxconnectionadvise"></a>AfxConnectionAdvise  
 Chiamare questa funzione per stabilire una connessione tra un'origine, specificata da `pUnkSrc`e un sink, specificato da `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD FAR* pdwCookie);
```  
  
### <a name="parameters"></a>Parametri  
 `pUnkSrc`  
 Puntatore all'oggetto che chiama l'interfaccia.  
  
 `pUnkSink`  
 Puntatore all'oggetto che implementa l'interfaccia.  
  
 `iid`  
 L'ID di interfaccia della connessione.  
  
 `bRefCount`  
 **TRUE** indica che la creazione della connessione deve provocare il conteggio dei riferimenti `pUnkSink` da incrementare. **FALSE** indica che il conteggio dei riferimenti non deve essere incrementato.  
  
 `pdwCookie`  
 Un puntatore a un `DWORD` in cui viene restituito un identificatore di connessione. Questo valore deve essere passato come il `dwCookie` parametro `AfxConnectionUnadvise` durante la disconnessione della connessione.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se è stata stabilita una connessione; in caso contrario 0.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCConnectionPoints n.&8;](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>Requisiti  
 **Intestazione:** afxctl. h 

##  <a name="afxconnectionunadvise"></a>AfxConnectionUnadvise  
 Chiamare questa funzione per disconnettere una connessione tra un'origine, specificata da `pUnkSrc`e un sink, specificato da `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD dwCookie); 
```  
  
### <a name="parameters"></a>Parametri  
 `pUnkSrc`  
 Puntatore all'oggetto che chiama l'interfaccia.  
  
 `pUnkSink`  
 Puntatore all'oggetto che implementa l'interfaccia.  
  
 `iid`  
 L'ID di interfaccia dell'interfaccia del punto di connessione.  
  
 `bRefCount`  
 **TRUE** indica che la disconnessione deve provocare il conteggio dei riferimenti `pUnkSink` deve essere diminuito. **FALSE** indica che non deve essere diminuito il conteggio dei riferimenti.  
  
 `dwCookie`  
 L'identificatore di connessione restituito da `AfxConnectionAdvise`.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se una connessione è stata interrotta; in caso contrario 0.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[9 NVC_MFCConnectionPoints](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>Requisiti  
 **Intestazione:** afxctl. h 

## <a name="see-also"></a>Vedere anche  
 [Macro e funzioni globali](../../mfc/reference/mfc-macros-and-globals.md)
