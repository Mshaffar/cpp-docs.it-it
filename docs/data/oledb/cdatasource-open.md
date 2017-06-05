---
title: "CDataSource::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataSource::Open"
  - "ATL.CDataSource.Open"
  - "CDataSource::Open"
  - "CDataSource.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open (metodo)"
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CDataSource::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Apre una connessione a un'origine dati usando un moniker **CLSID**, **ProgID** o `CEnumerator` oppure visualizza una richiesta all'utente con la finestra di dialogo di un localizzatore.  
  
## Sintassi  
  
```  
  
        HRESULT Open(  
   const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   HWND hWnd = GetActiveWindow( ),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET   
) throw( );  
HRESULT Open(   
   LPCWSTR szProgID,   
   DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(   
   LPCSTR szProgID,   
   LPCTSTR pName,   
   LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0   
) throw( );  
```  
  
#### Parametri  
 `clsid`  
 \[in\] **CLSID** del provider di dati.  
  
 *pPropSet*  
 \[in\] Puntatore a una matrice di strutture [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) che contiene le proprietà e i valori da impostare.  Vedere [Set di proprietà e gruppi di proprietà](https://msdn.microsoft.com/en-us/library/ms713696.aspx) nelle *informazioni di riferimento per programmatori OLE DB* in [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *nPropertySets*  
 \[in\] Numero di strutture [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) passate nell'argomento *pPropSet*.  
  
 *pName*  
 \[in\] Nome del database a cui connettersi.  
  
 *pUserName*  
 \[in\] Nome dell'utente.  
  
 *pPassword*  
 \[in\] Password dell'utente.  
  
 `nInitMode`  
 \[in\] Modalità di inizializzazione del database.  Per un elenco delle modalità di inizializzazione valide, vedere [Proprietà di inizializzazione](https://msdn.microsoft.com/en-us/library/ms723127.aspx) nelle *informazioni di riferimento per programmatori OLE DB* in [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  Se `nInitMode` è zero, nessuna modalità di inizializzazione è inclusa nel set di proprietà usato per aprire la connessione.  
  
 `szProgID`  
 \[in\] Identificatore di un programma.  
  
 `enumerator`  
 \[in\] Oggetto [CEnumerator](../../data/oledb/cenumerator-class.md) usato per ottenere un moniker per l'apertura della connessione quando il chiamante non specifica un oggetto **CLSID**.  
  
 `hWnd`  
 \[in\] Handle per la finestra che deve essere l'elemento padre della finestra di dialogo.  Se si usa l'overload della funzione che usa il parametro `hWnd`, verranno chiamati automaticamente i componenti del servizio. Per informazioni, vedere la sezione Note.  
  
 `dwPromptOptions`  
 \[in\] Determina lo stile della finestra di dialogo del localizzatore da visualizzare.  Per i possibili valori, vedere Msdasc.h.  
  
## Valore restituito  
 `HRESULT` standard.  
  
## Note  
 L'overload del metodo che usa il parametro `hWnd` apre un oggetto origine dati con i componenti del servizio in oledb32.dll. Questa DLL contiene l'implementazione delle funzionalità di Componenti del servizio, come il pool di risorse, l'inserimento automatico delle transazioni e così via.  Per altre informazioni, vedere "Servizi OLE DB" nelle informazioni di riferimento per programmatori OLE DB all'indirizzo [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
 Gli overload del metodo che non usano il parametro `hWnd` aprono un oggetto origine dati senza usare i componenti del servizio in oledb32.dll.  Un oggetto [CDataSource](../../data/oledb/cdatasource-class.md) aperto con questi overload della funzione non sarà in grado di utilizzare alcuna delle funzionalità dei componenti del servizio.  
  
## Esempio  
 Il codice seguente mostra come aprire un'origine dati Jet 4.0 con modelli OLE DB.  L'origine dati Jet deve essere considerata un'origine dati OLE DB.  Tuttavia, per la chiamata a **Open** sono necessari due set di proprietà: uno per **DBPROPSET\_DBINIT** e l'altro per **DBPROPSET\_JETOLEDB\_DBINIT**, in modo da poter impostare **DBPROP\_JETOLEDB\_DATABASEPASSWORD**.  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/CPP/cdatasource-open_1.cpp)]  
  
## Requisiti  
 **Intestazione:** atldbcli.h  
  
## Vedere anche  
 [Classe CDataSource](../../data/oledb/cdatasource-class.md)