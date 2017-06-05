---
title: Classe CDaoQueryDef | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
dev_langs:
- C++
helpviewer_keywords:
- QueryDef objects
- CDaoQueryDef class
- queries [Visual Studio], defining
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
caps.latest.revision: 24
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
ms.openlocfilehash: 0bf06c68bb7072aa1907e4c730848cca9ff5e7d0
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef (classe)
Rappresenta una definizione della query, o "querydef, in genere salvata in un database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CDaoQueryDef : public CObject  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|Costruisce un **CDaoQueryDef** oggetto. Quindi chiamare il metodo **aprire** o **crea**, a seconda delle esigenze.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CDaoQueryDef:: Append](#append)|Aggiunge l'oggetto querydef insieme QueryDefs del database come una query salvata.|  
|[CDaoQueryDef::CanUpdate](#canupdate)|Restituisce zero se la query è possibile aggiornare il database.|  
|[CDaoQueryDef::Close](#close)|Chiude l'oggetto querydef. Dopo aver terminato l'eliminazione dell'oggetto C++.|  
|[CDaoQueryDef::Create](#create)|Crea l'oggetto querydef DAO sottostante. Utilizzare l'oggetto querydef come una query temporanea o di chiamare **Append** per salvarlo nel database.|  
|[CDaoQueryDef:: Execute](#execute)|Esegue la query definita dall'oggetto querydef.|  
|[CDaoQueryDef::GetConnect](#getconnect)|Restituisce la stringa di connessione associata a tale oggetto. La stringa di connessione identifica l'origine dati. (Per SQL pass-through query solo; in caso contrario una stringa vuota.)|  
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|Restituisce la data che è stata creata la query salvata.|  
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|Restituisce la data che dell'ultimo aggiornamento query salvata.|  
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|Restituisce il numero di campi definiti dall'oggetto querydef.|  
|[CDaoQueryDef::GetFieldInfo](#getfieldinfo)|Restituisce informazioni su un campo specificato definito nella query.|  
|[CDaoQueryDef::GetName](#getname)|Restituisce il nome dell'oggetto querydef.|  
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|Restituisce il valore di timeout utilizzato da ODBC (per una query ODBC) quando viene eseguito l'oggetto querydef. Questo parametro determina il tempo per consentire di completamento dell'azione della query.|  
|[CDaoQueryDef::GetParameterCount](#getparametercount)|Restituisce il numero di parametri definiti per la query.|  
|[CDaoQueryDef::GetParameterInfo](#getparameterinfo)|Restituisce informazioni su un parametro specificato per la query.|  
|[CDaoQueryDef:: GetParamValue](#getparamvalue)|Restituisce il valore di un parametro specificato per la query.|  
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|Restituisce il numero di record interessati da una query.|  
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|Restituisce zero se la query definita dall'oggetto querydef restituisce i record.|  
|[CDaoQueryDef::GetSQL](#getsql)|Restituisce la stringa SQL che specifica la query definita dall'oggetto.|  
|[CDaoQueryDef::GetType](#gettype)|Restituisce il tipo di query: eliminare, aggiornare, Accodamento, creazione tabella e così via.|  
|[CDaoQueryDef::IsOpen](#isopen)|Restituisce zero se l'oggetto querydef è aperto e può essere eseguito.|  
|[CDaoQueryDef::Open](#open)|Apre un oggetto querydef esistente archiviato nella raccolta QueryDefs del database.|  
|[CDaoQueryDef::SetConnect](#setconnect)|Imposta la stringa di connessione per una query pass-through SQL in un'origine dati ODBC.|  
|[CDaoQueryDef::SetName](#setname)|Imposta il nome della query salvata, sostituendo il nome utilizzato quando è stato creato l'oggetto querydef.|  
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|Imposta il valore di timeout utilizzato da ODBC (per una query ODBC) quando viene eseguito l'oggetto querydef.|  
|[CDaoQueryDef:: SetParamValue](#setparamvalue)|Imposta il valore di un parametro specificato per la query.|  
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|Specifica se l'oggetto querydef restituisce i record. Impostare questo attributo su **TRUE** è valido solo per le query pass-through SQL.|  
|[CDaoQueryDef::SetSQL](#setsql)|Imposta la stringa SQL che specifica la query definita dall'oggetto.|  
  
### <a name="public-data-members"></a>Membri dati pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CDaoQueryDef::m_pDAOQueryDef](#m_pdaoquerydef)|Puntatore all'interfaccia OLE per l'oggetto querydef DAO sottostante.|  
|[CDaoQueryDef::m_pDatabase](#m_pdatabase)|Un puntatore per il `CDaoDatabase` oggetto a cui è associato l'oggetto querydef. Oggetto querydef potrebbe essere salvati nel database o meno.|  
  
## <a name="remarks"></a>Note  
 Un oggetto querydef è un oggetto di accesso ai dati che contiene l'istruzione SQL che descrive una query e le relative proprietà, ad esempio "Data creazione" e "Timeout ODBC". È inoltre possibile creare oggetti temporanei querydef senza salvarli, ma è consigliabile e molto più efficiente, per salvare comunemente riutilizzare le query in un database. Oggetto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) oggetto gestisce una raccolta denominata raccolta QueryDefs, che contiene il querydefs salvato.  
  
> [!NOTE]
>  Le classi di database DAO sono distinte dalle classi di database MFC basate su ODBC Open Database Connectivity (). Tutti i nomi delle classi di database DAO hanno il prefisso "CDao". È comunque possibile accedere alle origini dati ODBC con le classi DAO. In generale, le classi MFC basate su DAO sono più in grado di supportare più classi MFC basate su ODBC; le classi basate su DAO possono accedere ai dati, ad esempio tramite driver ODBC, tramite i propri motore di database. Le classi basate su DAO supportano anche operazioni linguaggio DDL (Data Definition), ad esempio l'aggiunta di tabelle tramite le classi, senza dover chiamare direttamente DAO.  
  
## <a name="usage"></a>Utilizzo  
 Utilizzare querydef oggetti sia per funzionare con una query salvata esistente o creare una nuova query o query temporanei salvato:  
  
1.  In tutti i casi, creare innanzitutto un `CDaoQueryDef` fornendo un puntatore all'oggetto di [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) dell'oggetto a cui appartiene la query.  
  
2.  Procedere come segue, a seconda di ciò che desidera:  
  
    -   Per utilizzare una query salvata esistente, chiamare l'oggetto querydef [aprire](#open) funzione membro, fornendo il nome della query salvata.  
  
    -   Per creare una nuova query salvata, chiamare l'oggetto querydef [crea](#create) funzione membro, fornendo il nome della query. Quindi chiamare [Append](#append) per salvare la query aggiungendolo alla raccolta QueryDefs del database. **Crea** inserisce l'oggetto querydef in uno stato aperto, in tal caso, dopo la chiamata **crea** non è necessario chiamare **aprire**.  
  
    -   Per creare un oggetto querydef temporaneo, chiamare **crea**. Passare una stringa vuota per il nome della query. Non chiamare **Append**.  
  
 Al termine dell'utilizzo di un oggetto querydef, chiamare il relativo [Chiudi](#close) membro di funzione; quindi eliminare l'oggetto querydef.  
  
> [!TIP]
>  Il modo più semplice per creare le query salvate viene a creare i file e archiviarli nel database utilizzando Microsoft Access. È quindi possibile aprire e utilizzarle nel codice MFC.  
  
## <a name="purposes"></a>A scopo  
 È possibile utilizzare un oggetto querydef per gli scopi seguenti:  
  
-   Per creare un `CDaoRecordset` oggetto  
  
-   Per chiamare l'oggetto **Execute** funzione membro per eseguire direttamente una query o una query pass-through SQL  
  
 È possibile utilizzare un oggetto querydef per qualsiasi tipo di query, tra cui scegliere, azione, a campi incrociati, delete, update, Accodamento, creazione tabella, definizione dei dati, pass-through SQL, union e query in blocco. Tipo di query è determinato dal contenuto dell'istruzione SQL che viene fornito. Per informazioni sui tipi di query, vedere il **Execute** e [GetType](#gettype) funzioni membro. Recordset vengono comunemente utilizzati per la restituzione riga esegue una query, in genere quelli che utilizzano il **Seleziona... DA** le parole chiave. **Eseguire** viene in genere utilizzato per le operazioni bulk. Per ulteriori informazioni, vedere [Execute](#execute) e [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
## <a name="querydefs-and-recordsets"></a>QueryDefs e Recordset  
 Utilizzare un oggetto querydef per creare un `CDaoRecordset` dell'oggetto, in genere creare o aprire un oggetto querydef come descritto in precedenza. Creare quindi un oggetto recordset, passando un puntatore all'oggetto querydef quando si chiama [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open). Tale oggetto che viene passato deve essere aperta. Per ulteriori informazioni, vedere la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 È possibile utilizzare un oggetto querydef per creare un recordset (l'utilizzo più comune per un oggetto querydef) a meno che non è nello stato aperto. Inserire l'oggetto querydef stato aperto chiamando il **aprire** o **crea**.  
  
## <a name="external-databases"></a>Database esterni  
 Gli oggetti QueryDef sono il modo migliore per utilizzare il sottolinguaggio SQL nativo di un motore di database esterno. Ad esempio, è possibile creare una query Transact SQL (come in Microsoft SQL Server) e archiviarlo in un oggetto querydef. Quando è necessario utilizzare una query SQL non si basa sul motore di database Microsoft Jet, è necessario fornire una stringa di connessione che punta all'origine dati esterna. Le query con stringhe di connessione valide ignorano il motore di database e passano la query direttamente al server di database esterno per l'elaborazione.  
  
> [!TIP]
>  Il modo migliore per utilizzare le tabelle ODBC consiste nel collegarli a un Microsoft Jet (. Database MDB).  
  
 Per informazioni correlate, vedere gli argomenti "QueryDef oggetto", "Raccolta QueryDefs" e "CdbDatabase Object" nel SDK di DAO.  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoQueryDef`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxdao. h  
  
##  <a name="append"></a>CDaoQueryDef:: Append  
 Chiamare questa funzione membro dopo la chiamata [crea](#create) per creare un nuovo oggetto querydef.  
  
```  
virtual void Append();
```  
  
### <a name="remarks"></a>Note  
 **Aggiungere** Salva l'oggetto querydef nel database aggiungendo l'oggetto alla raccolta QueryDefs del database. È possibile utilizzare l'oggetto querydef come oggetto temporaneo senza accodarlo, ma se si desidera salvare in modo permanente, è necessario chiamare **Append**.  
  
 Se si tenta di aggiungere un oggetto querydef temporaneo, MFC genera un'eccezione di tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="canupdate"></a>CDaoQueryDef::CanUpdate  
 Chiamare questa funzione membro per determinare se è possibile modificare l'oggetto querydef, ad esempio modificandone il nome o una stringa SQL.  
  
```  
BOOL CanUpdate();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se è consentito modificare querydef; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 È possibile modificare l'oggetto querydef se:  
  
-   Non è basato su un database è aperto in sola lettura.  
  
-   Si dispone delle autorizzazioni di aggiornamento per il database.  
  
     Ciò dipende se è stata implementata la funzionalità di sicurezza. MFC fornisce supporto per la protezione. è necessario implementare la chiamando direttamente DAO o mediante Microsoft Access. Vedere l'argomento "Proprietà Permissions" nella Guida di DAO.  
  
##  <a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef  
 Costruisce un **CDaoQueryDef** oggetto.  
  
```  
CDaoQueryDef(CDaoDatabase* pDatabase);
```  
  
### <a name="parameters"></a>Parametri  
 `pDatabase`  
 Un puntatore a un oggetto aperto [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) oggetto.  
  
### <a name="remarks"></a>Note  
 L'oggetto può rappresentare un oggetto querydef esistente archiviato nella raccolta QueryDefs del database, una nuova query da archiviare nella raccolta o una query temporanea, non devono essere archiviati. Il passaggio successivo dipende dal tipo di oggetto querydef:  
  
-   Se l'oggetto rappresenta un oggetto querydef esistente, chiamare l'oggetto [aprire](#open) funzione membro per l'inizializzazione.  
  
-   Se l'oggetto rappresenta un nuovo oggetto querydef deve essere salvato, chiamare l'oggetto [crea](#create) funzione membro. Aggiunge l'oggetto di raccolta QueryDefs del database. Chiamare quindi `CDaoQueryDef` le funzioni membro per impostare gli attributi dell'oggetto. Infine, chiamare [Append](#append).  
  
-   Se l'oggetto rappresenta un oggetto querydef temporaneo (che non devono essere salvati nel database), chiamare **crea**, passando una stringa vuota per il nome della query. Dopo la chiamata **crea**, inizializzare l'oggetto querydef impostando direttamente i relativi attributi. Non chiamare **Append**.  
  
 Per impostare gli attributi dell'oggetto querydef, è possibile utilizzare il [SetName](#setname), [SetSQL](#setsql), [SetConnect](#setconnect), [SetODBCTimeout](#setodbctimeout), e [SetReturnsRecords](#setreturnsrecords) funzioni membro.  
  
 Quando si termina con l'oggetto querydef, chiamare il relativo [Chiudi](#close) funzione membro. Se si dispone di un puntatore all'oggetto querydef, utilizzare il **eliminare** operatore per eliminare l'oggetto C++.  
  
##  <a name="close"></a>CDaoQueryDef::Close  
 Dopo aver utilizzato l'oggetto querydef, chiamare questa funzione membro.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Note  
 Chiudere l'oggetto querydef rilascia l'oggetto DAO sottostante ma non elimina l'oggetto querydef DAO salvato o C++ `CDaoQueryDef` oggetto. Questo non è identico [CDaoDatabase::DeleteQueryDef](../../mfc/reference/cdaodatabase-class.md#deletequerydef), che consente di eliminare l'oggetto querydef dalla raccolta QueryDefs del database in DAO (se non è un oggetto querydef temporaneo).  
  
##  <a name="create"></a>CDaoQueryDef::Create  
 Chiamare questa funzione membro per creare una nuova query salvata o una nuova query temporanea.  
  
```  
virtual void Create(
    LPCTSTR lpszName = NULL,  
    LPCTSTR lpszSQL = NULL);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszName`  
 Il nome univoco della query salvata nel database. Per informazioni dettagliate sulla stringa di, vedere l'argomento "Metodo CreateQueryDef" nella Guida di DAO. Se si accetta il valore predefinito, una stringa vuota, viene creato un oggetto querydef temporaneo. Tale query non viene salvata nella raccolta QueryDefs.  
  
 `lpszSQL`  
 La stringa SQL che definisce la query. Se si accetta il valore predefinito di **NULL**, in un secondo momento, è necessario chiamare [SetSQL](#setsql) per impostare la stringa. Fino ad allora, la query non è definita. Tuttavia, è possibile utilizzare la query definita per aprire un oggetto recordset. Per informazioni dettagliate, vedere la sezione Osservazioni. L'istruzione SQL deve essere definito prima di tale oggetto è possibile aggiungere alla raccolta QueryDefs.  
  
### <a name="remarks"></a>Note  
 Se si passa un nome in `lpszName`, sarà quindi possibile chiamare [Append](#append) salvare l'oggetto nella raccolta QueryDefs del database. In caso contrario, l'oggetto è un oggetto querydef temporaneo e non viene salvata. In entrambi i casi, l'oggetto querydef è nello stato aperto e si possono essere utilizzare per creare un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) dell'oggetto o chiamare l'oggetto querydef [Execute](#execute) funzione membro.  
  
 Se non si specifica un'istruzione SQL in `lpszSQL`, non è possibile eseguire la query con **Execute** ma è possibile utilizzare per creare un oggetto recordset. In tal caso, MFC utilizza l'istruzione SQL predefinita del recordset.  
  
##  <a name="execute"></a>CDaoQueryDef:: Execute  
 Chiamare questa funzione membro per eseguire la query definita dall'oggetto querydef.  
  
```  
virtual void Execute(int nOptions = dbFailOnError);
```  
  
### <a name="parameters"></a>Parametri  
 `nOptions`  
 Valore intero che determina le caratteristiche della query. Per informazioni correlate, vedere l'argomento "Esegui metodo" nella Guida di DAO. È possibile utilizzare l'operatore OR bit per bit ( **|**) per combinare le costanti seguenti per questo argomento:  
  
- **dbDenyWrite** Nega l'autorizzazione in scrittura ad altri utenti.  
  
- **dbInconsistent** aggiornamenti non coerenti.  
  
- **dbConsistent** aggiornamenti consistenti.  
  
- **dbSQLPassThrough** pass-through SQL. L'istruzione SQL deve essere passato a un database ODBC per l'elaborazione.  
  
- **dbFailOnError** il valore predefinito. Eseguire il rollback degli aggiornamenti se si verifica un errore e report di errore all'utente.  
  
- **dbSeeChanges** genera un errore di run-time se un altro utente modifica i dati che si sta modificando.  
  
> [!NOTE]
>  Per una spiegazione dei termini "incoerente" e "coerenti", vedere l'argomento "Esegui metodo" nella Guida di DAO.  
  
### <a name="remarks"></a>Note  
 QueryDef (oggetti) utilizzati per l'esecuzione in questo modo possono rappresentare solo uno dei seguenti tipi di query:  
  
-   Query  
  
-   Query pass-through SQL  
  
 **Eseguire** non funziona per le query che restituiscono record, ad esempio le query di selezione. **Eseguire** viene comunemente utilizzato per le query di operazione, ad esempio **aggiornamento**, **inserire**, o **SELECT INTO**, o per operazioni di data definition language (DDL).  
  
> [!TIP]
>  Il modo migliore per utilizzare le origini dati ODBC consiste nel collegare le tabelle di un Microsoft Jet (. Database MDB). Per ulteriori informazioni, vedere l'argomento "L'accesso a database esterni con DAO" nella Guida di DAO.  
  
 Chiamare il [GetRecordsAffected](#getrecordsaffected) funzione membro dell'oggetto querydef per determinare il numero di record interessati dall'ultima **Execute** chiamare. Ad esempio, `GetRecordsAffected` restituisce informazioni sul numero di record eliminati, aggiornati o inseriti durante l'esecuzione di una query. Il conteggio restituito non riflette le modifiche nelle tabelle correlate quando cascade aggiorna o Elimina sono attive.  
  
 Se si include sia **dbInconsistent** e **dbConsistent** o se non si include, il risultato è il valore predefinito, **dbInconsistent**.  
  
 **Eseguire** non restituisce un oggetto recordset. Utilizzando **Execute** su una query che seleziona i record determina MFC generare un'eccezione di tipo [CDaoException](../../mfc/reference/cdaoexception-class.md).  
  
##  <a name="getconnect"></a>CDaoQueryDef::GetConnect  
 Chiamare questa funzione membro per ottenere la stringa di connessione associata all'origine dati dell'oggetto querydef.  
  
```  
CString GetConnect();
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [CString](../../atl-mfc-shared/reference/cstringt-class.md) contenente la stringa di connessione per l'oggetto querydef.  
  
### <a name="remarks"></a>Note  
 Questa funzione viene utilizzata solo con origini dati ODBC e ad alcuni driver ISAM. Non viene utilizzato con Microsoft Jet (. Database MDB). In questo caso, `GetConnect` restituisce una stringa vuota. Per ulteriori informazioni, vedere [SetConnect](#setconnect).  
  
> [!TIP]
>  Il modo migliore per utilizzare le tabelle ODBC consiste nel collegarli a una. Database MDB. Per ulteriori informazioni, vedere l'argomento "L'accesso a database esterni con DAO" nella Guida di DAO.  
  
 Per informazioni sulle stringhe di connessione, vedere l'argomento "Proprietà connessione" nella Guida di DAO.  
  
##  <a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated  
 Chiamare questa funzione membro per ottenere la data di che creazione dell'oggetto querydef.  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) oggetto contenente la data e ora di creazione di tale oggetto.  
  
### <a name="remarks"></a>Note  
 Per informazioni correlate, vedere l'argomento "Proprietà DateCreated e LastUpdated" nella Guida di DAO.  
  
##  <a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated  
 Chiamata questa funzione membro per ottenere l'oggetto querydef la data dell'ultimo aggiornamento: quando le relative proprietà sono state modificate, ad esempio il nome, la stringa SQL o la relativa stringa di connessione.  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) oggetto contenente la data e ora dell'ultimo aggiornamento dell'oggetto.  
  
### <a name="remarks"></a>Note  
 Per informazioni correlate, vedere l'argomento "Proprietà DateCreated e LastUpdated" nella Guida di DAO.  
  
##  <a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount  
 Chiamare questa funzione membro per recuperare il numero di campi nella query.  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di campi definiti nella query.  
  
### <a name="remarks"></a>Note  
 `GetFieldCount`è utile per lo scorrimento in ciclo tutti i campi nell'oggetto. A tale scopo, utilizzare `GetFieldCount` in combinazione con [GetFieldInfo](#getfieldinfo).  
  
##  <a name="getfieldinfo"></a>CDaoQueryDef::GetFieldInfo  
 Chiamare questa funzione membro per ottenere i vari tipi di informazioni relative a un campo definito nell'oggetto.  
  
```  
void GetFieldInfo(
    int nIndex,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetFieldInfo(
    LPCTSTR lpszName,  
    CDaoFieldInfo& fieldinfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametri  
 `nIndex`  
 Indice in base zero del campo desiderato nella raccolta di campi dell'oggetto querydef, per la ricerca in base all'indice.  
  
 `fieldinfo`  
 Un riferimento a un `CDaoFieldInfo` oggetto che restituisce le informazioni richieste.  
  
 `dwInfoOptions`  
 Opzioni che specificano quali informazioni sul campo da recuperare. Le opzioni disponibili sono elencate di seguito insieme a ciò che provocano la restituzione della funzione:  
  
- `AFX_DAO_PRIMARY_INFO`(Impostazione predefinita) Nome, tipo, dimensioni, gli attributi  
  
- `AFX_DAO_SECONDARY_INFO`Informazioni principali più: posizione ordinale, richiesto, consentono di lunghezza Zero, campo di origine, il nome esterna, tabella di origine, ordine di ordinamento  
  
- `AFX_DAO_ALL_INFO`Più informazioni primarie e secondarie: valore predefinito, il testo di convalida, regola di convalida  
  
 `lpszName`  
 Stringa contenente il nome del campo desiderato, per la ricerca in base al nome. È possibile utilizzare un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Note  
 Per una descrizione delle informazioni restituite `fieldinfo`, vedere il [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) struttura. Questa struttura dispone di membri che corrispondono alle informazioni descrittive in `dwInfoOptions` sopra. Se si richiede un livello di informazioni, si ottengono livelli precedenti oltre a informazioni.  
  
##  <a name="getname"></a>CDaoQueryDef::GetName  
 Chiamare questa funzione membro per recuperare il nome della query rappresentato dall'oggetto.  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>Valore restituito  
 Nome della query.  
  
### <a name="remarks"></a>Note  
 QueryDef nomi sono nomi univoci definiti dall'utente. Per ulteriori informazioni sui nomi querydef, vedere l'argomento "Proprietà di nome" nella Guida di DAO.  
  
##  <a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout  
 Chiamare questa funzione membro per recuperare il limite di tempo corrente prima del timeout di una query a un'origine dati ODBC.  
  
```  
short GetODBCTimeout();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di secondi prima di una query timeout.  
  
### <a name="remarks"></a>Note  
 Per informazioni su questo limite di tempo, vedere l'argomento "Proprietà ODBCTimeout" nella Guida di DAO.  
  
> [!TIP]
>  Il modo migliore per utilizzare le tabelle ODBC consiste nel collegarli a un Microsoft Jet (. Database MDB). Per ulteriori informazioni, vedere l'argomento "L'accesso a database esterni con DAO" nella Guida di DAO.  
  
##  <a name="getparametercount"></a>CDaoQueryDef::GetParameterCount  
 Chiamare questa funzione membro per recuperare il numero di parametri nella query salvata.  
  
```  
short GetParameterCount();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di parametri definiti nella query.  
  
### <a name="remarks"></a>Note  
 `GetParameterCount`è utile per lo scorrimento in ciclo tutti i parametri nell'oggetto. A tale scopo, utilizzare `GetParameterCount` in combinazione con [GetParameterInfo](#getparameterinfo).  
  
 Per informazioni correlate, vedere gli argomenti "Parametro oggetto", "Raccolta di parametri" e "dichiarazione PARAMETERS (SQL)" nella Guida di DAO.  
  
##  <a name="getparameterinfo"></a>CDaoQueryDef::GetParameterInfo  
 Chiamare questa funzione membro per ottenere informazioni su un parametro definito nell'oggetto.  
  
```  
void GetParameterInfo(
    int nIndex,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

 
void GetParameterInfo(
    LPCTSTR lpszName,  
    CDaoParameterInfo& paraminfo,  
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```  
  
### <a name="parameters"></a>Parametri  
 `nIndex`  
 Indice in base zero del parametro desiderato nella raccolta di parametri dell'oggetto querydef, per la ricerca in base all'indice.  
  
 `paraminfo`  
 Un riferimento a un [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) oggetto che restituisce le informazioni richieste.  
  
 `dwInfoOptions`  
 Opzioni che specificano quali informazioni sul parametro da recuperare. L'opzione disponibile è incluso nell'elenco con la funzione restituire fa:  
  
- `AFX_DAO_PRIMARY_INFO`(Impostazione predefinita) Nome, tipo  
  
 `lpszName`  
 Stringa contenente il nome del parametro desiderato, per la ricerca in base al nome. È possibile utilizzare un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Note  
 Per una descrizione delle informazioni restituite `paraminfo`, vedere il [CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md) struttura. Questa struttura dispone di membri che corrispondono alle informazioni descrittive in `dwInfoOptions` sopra.  
  
 Per informazioni correlate, vedere l'argomento "dichiarazione PARAMETERS (SQL)" nella Guida di DAO.  
  
##  <a name="getparamvalue"></a>CDaoQueryDef:: GetParamValue  
 Chiamare questa funzione membro per recuperare il valore del parametro specificato memorizzata nella raccolta di parametri dell'oggetto corrente.  
  
```  
virtual COleVariant GetParamValue(LPCTSTR lpszName);  
virtual COleVariant GetParamValue(int nIndex);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszName`  
 Il nome del parametro il cui valore si desidera, per la ricerca in base al nome.  
  
 `nIndex`  
 Indice in base zero del parametro nella raccolta di parametri dell'oggetto querydef, per la ricerca in base all'indice. È possibile ottenere questo valore con chiamate a [GetParameterCount](#getparametercount) e [GetParameterInfo](#getparameterinfo).  
  
### <a name="return-value"></a>Valore restituito  
 Un oggetto della classe [COleVariant](../../mfc/reference/colevariant-class.md) che contiene il valore del parametro.  
  
### <a name="remarks"></a>Note  
 È possibile accedere il parametro in base al nome o la posizione ordinale nella raccolta.  
  
 Per informazioni correlate, vedere l'argomento "dichiarazione PARAMETERS (SQL)" nella Guida di DAO.  
  
##  <a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected  
 Chiamare questa funzione membro per determinare il numero di record interessato dall'ultima chiamata di [Execute](#execute).  
  
```  
long GetRecordsAffected();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di record interessati.  
  
### <a name="remarks"></a>Note  
 Il conteggio restituito non riflette le modifiche nelle tabelle correlate quando cascade aggiorna o Elimina sono attive.  
  
 Per ulteriori informazioni vedere l'argomento "Proprietà RecordsAffected" nella Guida di DAO.  
  
##  <a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords  
 Chiamare questa funzione membro per determinare se l'oggetto querydef è basata su una query che restituisce i record.  
  
```  
BOOL GetReturnsRecords();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se l'oggetto querydef è basato su una query che restituisce record. in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Questa funzione membro viene utilizzata solo per le query pass-through SQL. Per ulteriori informazioni sulle query SQL, vedere il [Execute](#execute) funzione membro. Per ulteriori informazioni sull'utilizzo di query pass-through SQL, vedere il [SetReturnsRecords](#setreturnsrecords) funzione membro.  
  
 Per informazioni correlate, vedere l'argomento "Proprietà Restituisci" nella Guida di DAO.  
  
##  <a name="getsql"></a>CDaoQueryDef::GetSQL  
 Chiamare questa funzione membro per recuperare l'istruzione SQL che definisce la query in cui si basa l'oggetto.  
  
```  
CString GetSQL();
```  
  
### <a name="return-value"></a>Valore restituito  
 L'istruzione SQL che definisce la query in cui si basa l'oggetto.  
  
### <a name="remarks"></a>Note  
 È quindi probabilmente analizza la stringa di parole chiave, i nomi delle tabelle e così via.  
  
 Per informazioni correlate, vedere gli argomenti "Proprietà SQL", "Confronto di Microsoft Jet Database Engine SQL e SQL ANSI" e "Esecuzione di query su un Database con in codice SQL" nella Guida di DAO.  
  
##  <a name="gettype"></a>CDaoQueryDef::GetType  
 Chiamare questa funzione membro per determinare il tipo di query di oggetto.  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il tipo della query definito dall'oggetto. Per i valori, vedere la sezione Osservazioni.  
  
### <a name="remarks"></a>Note  
 Il tipo di query è impostato da quello specificato nella stringa SQL dell'oggetto querydef quando si crea l'oggetto querydef o chiamare un oggetto querydef esistente [SetSQL](#setsql) funzione membro. Il tipo di query restituito da questa funzione può essere uno dei valori seguenti:  
  
- **dbQSelect** selezionare  
  
- **dbQAction** azione  
  
- **dbQCrosstab** a campi incrociati  
  
- **dbQDelete** eliminare  
  
- **dbQUpdate** aggiornamento  
  
- **dbQAppend** Append  
  
- **dbQMakeTable** tabella  
  
- **dbQDDL** definizione dei dati  
  
- **dbQSQLPassThrough** pass-through  
  
- **dbQSetOperation** unione  
  
- **dbQSPTBulk** utilizzato con **dbQSQLPassThrough** per specificare una query che restituisce record.  
  
> [!NOTE]
>  Per creare una query pass-through SQL, non impostare il **dbSQLPassThrough** costante. Questo viene impostato automaticamente dal motore di database Microsoft Jet quando si crea un oggetto querydef e impostare la stringa di connessione.  
  
 Per informazioni sulle stringhe SQL, vedere [GetSQL](#getsql). Per informazioni sui tipi di query, vedere [Execute](#execute).  
  
##  <a name="isopen"></a>CDaoQueryDef::IsOpen  
 Chiamare questa funzione membro per determinare se il `CDaoQueryDef` oggetto è aperto.  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se la `CDaoQueryDef` oggetto è aperto; in caso contrario, 0.  
  
### <a name="remarks"></a>Note  
 Un oggetto querydef deve essere aperta prima di utilizzarlo per chiamare [Execute](#execute) o per creare un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) oggetto. Per inserire un oggetto querydef in una chiamata aperta è [crea](#create) (per un nuovo oggetto querydef) o [aprire](#open) (per un oggetto querydef esistente).  
  
##  <a name="m_pdatabase"></a>CDaoQueryDef::m_pDatabase  
 Contiene un puntatore per il [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) oggetto associato all'oggetto querydef.  
  
### <a name="remarks"></a>Note  
 Utilizzare questo puntatore, se è necessario accedere direttamente al database, ad esempio, per ottenere puntatori ad altre querydef o recordset degli oggetti nelle raccolte del database.  
  
##  <a name="m_pdaoquerydef"></a>CDaoQueryDef::m_pDAOQueryDef  
 Contiene un puntatore all'interfaccia OLE per l'oggetto querydef DAO sottostante.  
  
### <a name="remarks"></a>Note  
 Questo puntatore viene fornito per motivi di completezza e la coerenza con le altre classi. Tuttavia, poiché MFC incapsula piuttosto completamente querydefs DAO, è molto improbabile che serve. Se si utilizza, procedere con cautela, in particolare, non modificare il valore del puntatore a meno che non si conosce l'operazione.  
  
##  <a name="open"></a>CDaoQueryDef::Open  
 Chiamare questa funzione membro per aprire un oggetto querydef salvato in precedenza nella raccolta QueryDefs del database.  
  
```  
virtual void Open(LPCTSTR lpszName = NULL);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszName`  
 Stringa che contiene il nome dell'oggetto querydef salvato per aprire. È possibile utilizzare un [CString](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="remarks"></a>Note  
 Una volta aperto l'oggetto querydef, è possibile chiamare il relativo [Execute](#execute) funzione membro oppure utilizzare l'oggetto querydef per creare un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) oggetto.  
  
##  <a name="setconnect"></a>CDaoQueryDef::SetConnect  
 Chiamare questa funzione membro per impostare la stringa di connessione dell'oggetto querydef.  
  
```  
void SetConnect(LPCTSTR lpszConnect);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszConnect`  
 Stringa che contiene una stringa di connessione per la proprietà associata [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) oggetto.  
  
### <a name="remarks"></a>Note  
 La stringa di connessione viene utilizzata per passare informazioni aggiuntive a ODBC e ad alcuni driver ISAM in base alle esigenze. Non è utilizzato per Microsoft Jet (. Database MDB).  
  
> [!TIP]
>  Il modo migliore per utilizzare le tabelle ODBC consiste nel collegarli a una. Database MDB.  
  
 Prima di eseguire un querydef che rappresenta una query pass-through SQL a un'origine dati ODBC, impostare la stringa di connessione con `SetConnect` e chiamare [SetReturnsRecords](#setreturnsrecords) per specificare se la query restituisce i record.  
  
 Per ulteriori informazioni sulla struttura e alcuni esempi di componenti di stringa di connessione della stringa di connessione, vedere l'argomento "Proprietà connessione" nella Guida di DAO.  
  
##  <a name="setname"></a>CDaoQueryDef::SetName  
 Chiamare questa funzione membro se si desidera modificare il nome di un oggetto querydef che non è temporaneo.  
  
```  
void SetName(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszName`  
 Stringa che contiene il nuovo nome per una query permanenti associato [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) oggetto.  
  
### <a name="remarks"></a>Note  
 QueryDef nomi sono nomi univoci, definito dall'utente. È possibile chiamare `SetName` prima querydef oggetto viene aggiunto alla raccolta QueryDefs.  
  
##  <a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout  
 Chiamare questa funzione membro per impostare il limite di tempo prima del timeout di una query a un'origine dati ODBC.  
  
```  
void SetODBCTimeout(short nODBCTimeout);
```  
  
### <a name="parameters"></a>Parametri  
 *nODBCTimeout*  
 Il numero di secondi prima di una query timeout.  
  
### <a name="remarks"></a>Note  
 Questa funzione membro consente di ignorare il numero predefinito di secondi prima che le operazioni successive nell'origine dati connessa "timeout". Un'operazione potrebbe essere un timeout a causa di problemi di accesso di rete, il tempo di elaborazione di un numero eccessivo di query e così via. Chiamare `SetODBCTimeout` prima di eseguire una query con questo querydef se si desidera modificare il valore di timeout di query. (Come ODBC Riutilizza le connessioni, il valore di timeout è lo stesso per tutti i client nella stessa connessione.)  
  
 Il valore predefinito di timeout delle query è 60 secondi.  
  
##  <a name="setparamvalue"></a>CDaoQueryDef:: SetParamValue  
 Chiamare questa funzione membro per impostare il valore di un parametro nell'oggetto in fase di esecuzione.  
  
```  
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszName`  
 Il nome del parametro il cui valore si desidera impostare.  
  
 `varValue`  
 Il valore da impostare; vedere la sezione Osservazioni.  
  
 `nIndex`  
 La posizione ordinale del parametro nella raccolta di parametri dell'oggetto querydef. È possibile ottenere questo valore con chiamate a [GetParameterCount](#getparametercount) e [GetParameterInfo](#getparameterinfo).  
  
### <a name="remarks"></a>Note  
 Il parametro deve già sono stato definito come parte della stringa SQL dell'oggetto querydef. È possibile accedere il parametro in base al nome o la posizione ordinale nella raccolta.  
  
 Specificare il valore da impostare come un `COleVariant` oggetto. Per informazioni sull'impostazione il valore desiderato e digitare il `COleVariant` oggetto, vedere la classe [COleVariant](../../mfc/reference/colevariant-class.md).  
  
##  <a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords  
 Chiamare questa funzione membro come parte del processo di configurazione di una query pass-through SQL a un database esterno.  
  
```  
void SetReturnsRecords(BOOL bReturnsRecords);
```  
  
### <a name="parameters"></a>Parametri  
 *bReturnsRecords*  
 Passare **TRUE** se la query su un database esterno restituisce record; in caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Note  
 In tal caso, è necessario creare l'oggetto querydef e impostarne le proprietà mediante altri `CDaoQueryDef` funzioni membro. Per una descrizione di database esterni, vedere [SetConnect](#setconnect).  
  
##  <a name="setsql"></a>CDaoQueryDef::SetSQL  
 Chiamare questa funzione membro per impostare l'istruzione SQL che esegue l'oggetto querydef.  
  
```  
void SetSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszSQL`  
 Stringa contenente un'istruzione SQL completa, adatta per l'esecuzione. La sintassi della stringa dipende da DBMS che le destinazioni di query. Per una descrizione della sintassi utilizzata nel motore di database Microsoft Jet, vedere l'argomento "Creazione istruzioni nel codice SQL" nella Guida di DAO.  
  
### <a name="remarks"></a>Note  
 Un tipico utilizzo di `SetSQL` è l'impostazione di un oggetto querydef per l'utilizzo in una query pass-through SQL. (Per la sintassi delle query pass-through SQL nel DBMS di destinazione, vedere la documentazione per il DBMS).  
  
## <a name="see-also"></a>Vedere anche  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [CDaoRecordset (classe)](../../mfc/reference/cdaorecordset-class.md)   
 [CDaoDatabase (classe)](../../mfc/reference/cdaodatabase-class.md)   
 [Classe CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Classe CDaoException](../../mfc/reference/cdaoexception-class.md)
