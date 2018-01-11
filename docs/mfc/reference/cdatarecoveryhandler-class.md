---
title: Classe CDataRecoveryHandler | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
dev_langs: C++
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35ede62ddb5fcfbc32fec37322985d40fffbbe44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="cdatarecoveryhandler-class"></a>Classe CDataRecoveryHandler
Il `CDataRecoveryHandler` esegue i documenti e le ripristina se un'applicazione viene chiusa in modo imprevisto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CDataRecoveryHandler : public CObject  
```  
  
## <a name="members"></a>Membri  
  
### <a name="constructors"></a>Costruttori  
  
|||  
|-|-|  
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Costruisce un oggetto `CDataRecoveryHandler`.|  
  
### <a name="methods"></a>Metodi  
  
|||  
|-|-|  
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Funzionalità di ogni file registrato con il `CDataRecoveryHandler` classe.|  
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Esegue il documento specificato.|  
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Aggiunge un documento all'elenco dei documenti aperti.|  
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Elimina tutti i file più corrente.|  
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Elimina il file specificato salvata automaticamente.|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Genera il nome di un file di salvataggio automatico associato con il nome del file documento fornito.|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Restituisce l'intervallo tra tentativi di salvataggio automatico.|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Restituisce il percorso dei file salvata automaticamente.|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Recupera il nome del documento da un `CDocument` oggetto.|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Recupera il titolo normale per il documento specificato.|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crea e restituisce il titolo per il documento recuperato.|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Recupera l'identificatore univoco di riavvio per l'applicazione.|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indica se il `CDataRecoveryHandler` esegue un salvataggio automatico nel ciclo inattivo corrente.|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indica se Gestione riavvio ha provocato la chiusura dell'applicazione.|  
|[CDataRecoveryHandler::Initialize](#initialize)|Inizializza `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Visualizza una finestra di dialogo per l'utente per ogni documento di `CDataRecoveryHandler` salvata automaticamente. Nella finestra di dialogo determina se l'utente desidera ripristinare il documento salvata automaticamente.|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Carica l'elenco di documenti aperti dal Registro di sistema.|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Rimuove il documento fornito dall'elenco di documenti aperti.|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Apre i documenti aperti in precedenza.|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Ripristina i documenti salvata automaticamente in base all'input utente.|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Salva l'elenco corrente dei documenti aperti nel Registro di sistema di Windows.|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Imposta il tempo tra cicli di salvataggio automatico in millisecondi.|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Imposta la directory in cui sono archiviati i file salvata automaticamente.|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Imposta l'identificatore univoco di riavvio per questa istanza di `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Imposta se la `CDataRecoveryHandler` Salva le informazioni sui documenti aperti nel Registro di sistema di Windows durante il ciclo inattivo corrente.|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Imposta se l'uscita dell'applicazione precedente è stato causato da Gestione riavvio.|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Aggiorna le informazioni per un documento perché l'utente lo stato salvato.|  
  
### <a name="data-members"></a>Membri di dati  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|Indica se il gestore di ripristino dati riapre documenti precedentemente aperti.|  
|m_bSaveDocumentInfoOnIdle|Indica se la funzionalità di gestore dati ripristino documenti nel successivo ciclo inattivo.|  
|m_bShutdownByRestartManager|Indica se Gestione riavvio determina la chiusura dell'applicazione.|  
|m_dwRestartManagerSupportFlags|Flag che indicano quali supportano Gestione riavvio fornisce per l'applicazione.|  
|m_lstAutosavesToDelete|Un elenco di più file che non sono stati eliminati quando i documenti originali sono stati chiusi. Quando termina l'applicazione, i tentativi di riavvio manager l'eliminazione dei file.|  
|m_mapDocNameToAutosaveName|Mappa i nomi dei documenti per i nomi dei file salvata automaticamente.|  
|m_mapDocNameToDocumentPtr|Mappa i nomi dei documenti per il [CDocument](../../mfc/reference/cdocument-class.md) puntatori.|  
|m_mapDocNameToRestoreBool|Mappa i nomi dei documenti per un parametro booleano che indica se si desidera ripristinare il documento salvata automaticamente.|  
|m_mapDocumentPtrToDocName|Una mappa del `CDocument` puntatori per i nomi dei documenti.|  
|m_mapDocumentPtrToDocTitle|Una mappa del `CDocument` puntatori per i titoli del documento. Questi titoli vengono utilizzati per il salvataggio dei file.|  
|m_nAutosaveInterval|Tempo in millisecondi tra le funzionalità.|  
|m_nTimerID|L'identificatore per il timer di salvataggio automatico.|  
|m_strAutosavePath|Il percorso in cui sono archiviati i documenti salvata automaticamente.|  
|m_strRestartIdentifier|Rappresentazione di stringa di un GUID per il gestore di riavvio.|  
  
## <a name="remarks"></a>Note  
 Gestione riavvio utilizza la `CDataRecoveryHandler` classe mantenere tenerne traccia di tutti i documenti aperti e salvataggio automatico in base alle esigenze. Per abilitare il salvataggio automatico, usare il [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) metodo. Questo metodo indirizza il `CDataRecoveryHandler` per eseguire un salvataggio automatico nel successivo ciclo inattivo. Le chiamate di Gestione riavvio `SetSaveDocumentInfoOnIdle` quando il `CDataRecoveryHandler` deve eseguire un salvataggio automatico.  
  
 Tutti i metodi del `CDataRecoveryHandler` classe sono virtuali. L'override dei metodi in questa classe per creare il proprio gestore di ripristino di dati personalizzati. A meno che non si crea un proprio gestore di ripristino di dati o riavviare la gestione, non creare un'istanza di un CDataRecoveryHandler. Il [CWinApp (classe)](../../mfc/reference/cwinapp-class.md) crea un `CDataRecoveryHandler` dell'oggetto come richiesto.  
  
 Prima di poter usare un `CDataRecoveryHandler` dell'oggetto, è necessario chiamare [CDataRecoveryHandler::Initialize](#initialize).  
  
 Poiché il `CDataRecoveryHandler` classe è strettamente connessa a Gestione riavvio, `CDataRecoveryHandler` dipende dal parametro globale `m_dwRestartManagerSupportFlags`. Questo parametro determina quali autorizzazioni dispone di Gestione riavvio e l'interazione con l'applicazione. Per incorporare Gestione riavvio di un'applicazione esistente, è necessario assegnare `m_dwRestartManagerSupportFlags` il valore appropriato nel costruttore dell'applicazione principale. Per ulteriori informazioni su come usare Gestione riavvio, vedere [procedura: aggiungere supporto Gestione riavvio](../../mfc/how-to-add-restart-manager-support.md).  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo  
 Funzionalità di ogni file registrato con il `CDataRecoveryHandler` classe.  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se il `CDataRecoveryHandler` salvati tutti i documenti; `FALSE` se non è stato salvato un documento.  
  
### <a name="remarks"></a>Note  
 Questo metodo restituisce `TRUE` se vi sono documenti che devono essere salvati. Restituisce inoltre `TRUE` senza salvare i documenti se il recupero di `CWinApp` o `CDocManager` per l'applicazione genera un errore.  
  
 Utilizzare questo metodo, ovvero `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL` deve essere impostata in `m_dwRestartManagerSupportFlags`. Vedere [m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags) per ulteriori informazioni.  
  
##  <a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo  
 Esegue il documento specificato.  
  
```  
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,  
    BOOL bResetModifiedFlag = TRUE);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `pDocument`|Un puntatore al `CDocument` salvare.|  
|[in] `bResetModifiedFlag`|`TRUE`indica che il `CDataRecoveryHandler` considera `pDocument` per essere modificato. `FALSE` indica che il framework considera `pDocument` per essere modificata. Per ulteriori informazioni sull'effetto di questo flag, vedere la sezione Osservazioni.|  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se i flag appropriati sono impostati e `pDocument` valido `CDocument` oggetto.  
  
### <a name="remarks"></a>Note  
 Ogni `CDocument` oggetto dispone di un flag che indica se è stato modificato dopo l'ultimo salvataggio. Utilizzare [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) per determinare lo stato del flag. Se un `CDocument` non è stato modificato dopo l'ultimo salvataggio, `AutosaveDocumentInfo` Elimina tutti i file per il documento salvata automaticamente. Se un documento è stato modificato dall'ultimo salvataggio, la chiusura, viene richiesto all'utente di salvare il documento prima della chiusura.  
  
> [!NOTE]
>  Utilizzando `bResetModifiedFlag` per impostare lo stato del documento non modificato l'utente potrebbe perdere i dati non salvati. Se il framework considera un documento non modificato, la chiusura, non richiede all'utente di salvare.  
  
 Questo metodo genera un'eccezione con il [ASSERT](diagnostic-services.md#assert) macro se `pDocument` non è un valido `CDocument` oggetto.  
  
 Utilizzare questo metodo, ovvero `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` deve essere impostata in `m_dwRestartManagerSupportFlags`.   
  
##  <a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler  
 Costruisce un oggetto `CDataRecoveryHandler`.  
  
```  
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,  
    int nAutosaveInterval);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `dwRestartManagerSupportFlags`|Indica quali opzioni di Gestione riavvio sono supportate.|  
|[in] `nAutosaveInterval`|Tempo trascorso tra funzionalità. Questo parametro è espresso in millisecondi.|  
  
### <a name="remarks"></a>Note  
 Il framework MFC crea automaticamente un `CDataRecoveryHandler` oggetto per l'applicazione quando si utilizza il **nuovo progetto** procedura guidata. A meno che non si desidera personalizzare il comportamento di ripristino di dati o Gestione riavvio, non è necessario creare un `CDataRecoveryHandler` oggetto.  
  
  
##  <a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo  
 Aggiunge un documento all'elenco dei documenti aperti.  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `pDocument`|Un puntatore a un `CDocument`. Questo metodo crea le informazioni sul documento per questo `CDocument`.|  
  
### <a name="return-value"></a>Valore restituito  
 L'implementazione predefinita restituisce `TRUE`.  
  
### <a name="remarks"></a>Note  
 Questo metodo controlla se `pDocument` è già presente nell'elenco dei documenti prima di aggiungere il documento. Se `pDocument` è già nell'elenco, questo metodo elimina il file salvata automaticamente associato `pDocument`.  
  
 Utilizzare questo metodo, ovvero `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` deve essere impostata in `m_dwRestartManagerSupportFlags`. 
  
##  <a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles  
 Elimina tutti i file più corrente.  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>Valore restituito  
 L'implementazione predefinita restituisce sempre `TRUE`.  
  
##  <a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile  
 Elimina il file specificato salvata automaticamente.  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `strAutosavedFile`|Stringa che contiene il nome del file salvata automaticamente.|  
  
### <a name="return-value"></a>Valore restituito  
 L'implementazione predefinita restituiscono sempre `TRUE`.  
  
### <a name="remarks"></a>Note  
 Se questo metodo non è possibile eliminare il file di più, il nome del file vengono salvati in un elenco. Il distruttore per la `CDataRecoveryHandler` tenta di eliminare ogni file salvata automaticamente specificato nell'elenco.  
  
##  <a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName  
 Genera il nome di un file di salvataggio automatico associato con il nome del file documento fornito.  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [in] `strDocumentName`  
 Stringa che contiene il nome del documento. `GenerateAutosaveFileName`Usa il nome del documento per generare un nome di file corrispondente di salvataggio automatico.  
  
### <a name="return-value"></a>Valore restituito  
 Il nome del file di salvataggio automatico generato da `strDocumentName`.  
  
### <a name="remarks"></a>Note  
 Nome di ogni documento ha un mapping uno a uno con un nome di file di salvataggio automatico.  
  
##  <a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval  
 Restituisce l'intervallo tra tentativi di salvataggio automatico.  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Prova il numero di millisecondi compresi tra salvataggio automatico.  
  
##  <a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath  
 Restituisce il percorso dei file salvata automaticamente.  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il percorso in cui sono archiviati i documenti salvata automaticamente.  
  
##  <a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName  
 Recupera il nome del documento da un `CDocument` oggetto.  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `pDocument`|Un puntatore a un `CDocument`. `GetDocumentListName`Recupera il nome del documento da questo `CDocument`.|  
  
### <a name="return-value"></a>Valore restituito  
 Il nome del documento da `pDocument`.  
  
### <a name="remarks"></a>Note  
 Il `CDataRecoveryHandler` utilizza il nome del documento come chiave in `m_mapDocNameToAutosaveName`, `m_mapDocNameToDocumentPtr`, e `m_mapDocNameToRestoreBool`. Questi parametri consentono di `CDataRecoveryHandler` per monitorare `CDocument` oggetti, il nome del file di salvataggio automatico e le impostazioni con salvataggio automatico.  
  
##  <a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle  
 Recupera il titolo normale per il documento specificato.  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `pDocument`|Un puntatore a un `CDocument`.|  
  
### <a name="return-value"></a>Valore restituito  
 Il titolo normale per il documento specificato.  
  
### <a name="remarks"></a>Note  
 In genere, il titolo di un documento normale è il nome del file del documento senza il percorso. Titolo nel **nome File** campo il **Salva con nome** la finestra di dialogo.  
  
##  <a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle  
 Crea e restituisce il titolo per il documento recuperato.  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>Parametri  
 [in] `strDocumentTitle`  
 Il titolo normale per il documento.  
  
### <a name="return-value"></a>Valore restituito  
 Il titolo del documento recuperato.  
  
### <a name="remarks"></a>Note  
 Per impostazione predefinita, il titolo di un documento recuperato è il titolo normale con **[recuperato]** aggiunte. Il titolo recuperato viene visualizzato all'utente quando il `CDataRecoveryHandler` chiede all'utente di ripristinare più documenti.  
  
##  <a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier  
 Recupera l'identificatore univoco di riavvio per l'applicazione.  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Identificatore univoco di riavvio.  
  
### <a name="remarks"></a>Note  
 L'identificatore di riavvio è univoco per ogni esecuzione dell'applicazione.  
  
 Il `CDataRecoveryHandler` archivia le informazioni nel Registro di sistema relativi ai documenti attualmente aperti. Quando Gestione riavvio uscire da un'applicazione e lo riavvia, fornisce l'identificatore del riavvio di `CDataRecoveryHandler`. Il `CDataRecoveryHandler` utilizza l'identificatore di riavvio per recuperare l'elenco di documenti precedentemente aperti. In questo modo il `CDataRecoveryHandler` per tentare di individuare e ripristinare i file salvata automaticamente.  
  
##  <a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 Indica se il `CDataRecoveryHandler` esegue un salvataggio automatico nel ciclo inattivo corrente.  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`indica il `CDataRecoveryHandler` esegue il ciclo inattivo corrente; `FALSE` indica che non è presente.  
  
##  <a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager  
 Indica se Gestione riavvio ha provocato la chiusura dell'applicazione.  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`indica che la gestione riavvio ha provocato la chiusura; dell'applicazione `FALSE` indica non è stato eseguito.  
  
##  <a name="initialize"></a>CDataRecoveryHandler::Initialize  
 Inizializza `CDataRecoveryHandler`.  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se l'inizializzazione ha esito positivo; in caso contrario `FALSE`.  
  
### <a name="remarks"></a>Note  
 Il processo di inizializzazione carica il percorso per archiviare i file di salvataggio automatico dal Registro di sistema. Se il `Initialize` metodo non è possibile trovare la directory o se il percorso è `NULL`, `Initialize` ha esito negativo e restituisce `FALSE`.  
  
 Utilizzare [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) per modificare il percorso di salvataggio automatico, dopo l'applicazione Inizializza il `CDataRecoveryHandler`.  
  
 Il `Initialize` metodo inoltre avviato un timer per il monitoraggio quando si verifica il successivo salvataggio. Utilizzare [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) per modificare l'intervallo di salvataggio automatico, dopo l'applicazione Inizializza il `CDataRecoveryHandler`.  
  
##  <a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 Visualizza una finestra di dialogo per l'utente per ogni documento di `CDataRecoveryHandler` salvata automaticamente. Nella finestra di dialogo determina se l'utente desidera ripristinare il documento salvata automaticamente.  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>Note  
 Se l'applicazione è Unicode, questo metodo consente di visualizzare un [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) all'utente. In caso contrario, il framework utilizza [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) per chiedere all'utente.  
  
 Dopo aver `QueryRestoreAutosavedDocuments` raccoglie tutte le risposte dell'utente, archivia le informazioni nella variabile membro `m_mapDocNameToRestoreBool`. Questo metodo non ripristina i documenti salvata automaticamente.  
  
##  <a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList  
 Carica l'elenco di documenti aperti dal Registro di sistema.  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`indica che `ReadOpenDocumentList` caricato le informazioni per almeno un documento dal Registro di sistema. `FALSE` indica nessuna informazione di documento è stata caricata.  
  
### <a name="remarks"></a>Note  
 Questa funzione Carica le informazioni di documento aperto dal Registro di sistema e archiviarlo nella variabile membro `m_mapDocNameToAutosaveName`.  
  
 Dopo aver `ReadOpenDocumentList` carica tutti i dati, Elimina le informazioni sul documento dal Registro di sistema.  
  
##  <a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo  
 Rimuove il documento fornito dall'elenco di documenti aperti.  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `pDocument`|Puntatore al documento da rimuovere.|  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se `pDocument` è stato rimosso dall'elenco. `FALSE` se si è verificato un errore.  
  
### <a name="remarks"></a>Note  
 Quando l'utente chiude un documento, il framework utilizza questo metodo per rimuoverlo dall'elenco dei documenti aperti.  
  
 Se `RemoveDocumentInfo` non è possibile trovare `pDocument` nell'elenco dei documenti aperti, non esegue alcuna operazione e restituisce `TRUE`.  
  
 Utilizzare questo metodo, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` deve essere impostata in `m_dwRestartManagerSupportFlags`.   
  
##  <a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments  
 Apre i documenti aperti in precedenza.  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se almeno un documento è stato aperto. in caso contrario `FALSE`.  
  
### <a name="remarks"></a>Note  
 Questo metodo apre il salvataggio di documenti precedentemente aperti più recente. Se non è stato salvato un documento o più, `ReopenPreviousDocuments` apre un documento vuoto in base al modello per il tipo di file.  
  
 Utilizzare questo metodo, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` deve essere impostata in `m_dwRestartManagerSupportFlags`. Se questo parametro non è impostato, `ReopenPreviousDocuments` non esegue alcuna operazione e restituisce `FALSE`.  
  
 Se vi sono documenti archiviati nell'elenco di documenti precedentemente aperti, `ReopenPreviousDocuments` non esegue alcuna operazione e restituisce `FALSE`.  
  
##  <a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments  
 Ripristina i documenti salvata automaticamente in base all'input utente.  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se questo metodo ripristina correttamente i documenti.  
  
### <a name="remarks"></a>Note  
 Questo metodo chiama [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) per determinare che documenta l'utente desidera ripristinare. Se si decide di non ripristinare un documento più `RestoreAutosavedDocuments` Elimina il file di salvataggio automatico. In caso contrario, `RestoreAutosavedDocuments` sostituisce il documento aperto con la versione salvata automaticamente.  
  
 Utilizzare questo metodo, ovvero `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` o `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES` deve essere impostata in `m_dwRestartManagerSupportFlags`.   
  
##  <a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList  
 Salva l'elenco corrente dei documenti aperti nel Registro di sistema di Windows.  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se sono non presenti salvare i documenti aperti o sono stati salvati correttamente. `FALSE`Se sono presenti documenti per salvare il Registro di sistema, ma non sono state salvate perché si è verificato un errore.  
  
### <a name="remarks"></a>Note  
 Le chiamate di Gestione riavvio `SaveOpenDocumentList` quando l'applicazione viene chiusa in modo imprevisto o quando viene chiusa per un aggiornamento. Quando l'applicazione viene riavviata, utilizza [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) per recuperare l'elenco dei documenti aperti.  
  
 Questo metodo salva solo l'elenco dei documenti aperti. Il metodo [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) è responsabile per il salvataggio di documenti stessi.  
  
##  <a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval  
 Imposta il tempo tra cicli di salvataggio automatico in millisecondi.  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>Parametri  
 [in] `nAutosaveInterval`  
 Il nuovo intervallo di salvataggio automatico in millisecondi.  
  
##  <a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath  
 Imposta la directory in cui sono archiviati i file salvata automaticamente.  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `strAutosavePath`|Il percorso in cui sono archiviati i file di salvataggio automatico.|  
  
### <a name="remarks"></a>Note  
 Modifica della directory di salvataggio automatico non spostare attualmente più file.  
  
##  <a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier  
 Imposta l'identificatore univoco di riavvio per questa istanza di `CDataRecoveryHandler`.  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `strRestartIdentifier`|Identificatore univoco per il gestore di riavvio.|  
  
### <a name="remarks"></a>Note  
 Gestione riavvio registra le informazioni sui documenti aperti nel Registro di sistema. Queste informazioni vengono archiviate con l'identificatore univoco di riavvio come chiave. Poiché l'identificatore di riavvio è univoco per ogni istanza di un'applicazione, chiusura imprevista di più istanze di un'applicazione e Gestione riavvio è possibile ripristinare ognuno di essi.  
  
##  <a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 Imposta se la `CDataRecoveryHandler` Salva le informazioni sui documenti aperti nel Registro di sistema di Windows durante il ciclo inattivo corrente.  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `bSaveOnIdle`|`TRUE`Per salvare le informazioni documento durante il ciclo inattivo corrente. `FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager  
 Imposta se l'uscita dell'applicazione precedente è stato causato da Gestione riavvio.  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `bShutdownByRestartManager`|`TRUE`per indicare che il gestore di riavvio ha provocato la chiusura; dell'applicazione `FALSE` per indicare che l'applicazione è stato terminato per un altro motivo.|  
  
### <a name="remarks"></a>Note  
 Il framework si comporta in modo diverso in base a exit precedente non era previsto o sia stata avviata dal gestore di riavvio.  
  
##  <a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo  
 Aggiorna le informazioni per un documento perché l'utente lo stato salvato.  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `pDocument`|Puntatore al documento salvato.|  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se questo metodo eliminato il documento salvata automaticamente e aggiornata le informazioni del documento. `FALSE` se si è verificato un errore.  
  
### <a name="remarks"></a>Note  
 Quando un utente salva un documento, l'applicazione rimuove il file salvata automaticamente perché non è più necessario. `UpdateDocumentInfo`Elimina il file salvata automaticamente chiamando [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`Aggiunge quindi le informazioni da `pDocument` all'elenco di attualmente aprire documenti perché `RemoveDocumentInfo` elimina tali informazioni, ma salvati documento è ancora aperto.  
  
 Utilizzare questo metodo, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` deve essere impostata in `m_dwRestartManagerSupportFlags`.   
  
## <a name="see-also"></a>Vedere anche  
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Procedura: Aggiungere il supporto di Gestione riavvio](../../mfc/how-to-add-restart-manager-support.md)
