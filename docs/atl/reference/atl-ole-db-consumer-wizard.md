---
title: Creazione guidata Consumer OLE DB ATL | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: 13
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6e35ce9038a8fd8f7aeeb00139511a8f45c1257d
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="atl-ole-db-consumer-wizard"></a>Creazione guidata consumer OLE DB ATL
Questa procedura guidata imposta una classe consumer OLE DB con le associazioni dati necessaria accedere all'origine dati specificata tramite il provider OLE DB specificato.  
  
> [!NOTE]
>  Questa procedura guidata è necessario fare clic il **origine dati** pulsante per selezionare un'origine dati prima di immettere i nomi nel `Class` e **h** campi.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Origine dati**  
 Il **origine dati** pulsante consentono di configurare l'origine dati specificata utilizzando il provider OLE DB specificato. Quando si fa clic su questo pulsante, il **proprietà di Data Link** viene visualizzata la finestra di dialogo. Per ulteriori informazioni sulla creazione di stringhe di connessione e il **proprietà di Data Link** la finestra di dialogo, vedere [Data Link API Overview](https://msdn.microsoft.com/library/ms718102.aspx) nel [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)] documentazione.  
  
> [!NOTE]
>  Nelle versioni precedenti, fare clic su MAIUSC il **origine dati** pulsante aperta una finestra di dialogo Apri File per consentire di selezionare un file di Data Link (UDL). Questa funzionalità non è più supportata.  
  
 Nella finestra di dialogo è presenti quattro schede:  
  
- **Provider** scheda  
  
- **Connessione** scheda  
  
- **Advanced** scheda  
  
- **Tutti** scheda  
  
     Le seguenti informazioni aggiuntive vengono descritte le schede di **proprietà di Data Link** la finestra di dialogo.  
  
     Fare clic su **OK** alla fine. Il **Seleziona oggetto di Database** viene visualizzata la finestra di dialogo. Questa finestra di dialogo, selezionare la tabella, vista o stored procedure che verranno utilizzate dal consumer.  
  
 **Provider**  
     Selezionare un provider appropriato per gestire la connessione all'origine dati. Il tipo di provider è in genere determinato dal tipo di database a cui ci si connette. Fare clic su di `Next` pulsante oppure fare clic su di **connessione** scheda.  
  
 **Connessione**  
     Il contenuto di questa scheda dipende dal provider selezionato. Anche se esistono molti tipi di provider, in questa sezione vengono illustrate le connessioni per i due più comuni: dati ODBC e SQL. Gli altri sono simili a quelli nei campi descritti di seguito.  
  
     Per i dati SQL:  
  
    1. **Selezionare o immettere un nome server:** fare clic sul menu a discesa per visualizzare tutti i server di dati registrati nella rete e selezionarne uno.  
  
    2. **Immettere le informazioni per accedere al server:** immettere un nome utente e password per accedere al server dati.  
  
    3. **Selezionare il database nel server:** fare clic sul menu a discesa per visualizzare tutti i database registrati sul server di data e selezionare uno.  
  
         -oppure-  
  
 **Collegare un file di database come un nome di database:** specificare un file da utilizzare come database, immettere il nome percorso esplicito.  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **Utilizzare la sicurezza integrata di Windows NT**  
  
 **Usa nome utente e password**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **Nome dell'origine dati di utilizzo:** questo elenco a discesa vengono visualizzate origini dati registrate nel computer in uso. È possibile impostare le origini dati anticipo tramite Amministrazione origine dati ODBC- o -**Usa stringa di connessione:** viene immessa una stringa di connessione sia già stato ottenuto o fare clic su di **compilare** pulsante; il **selezionare un'origine dati** viene visualizzata la finestra di dialogo. Selezionare un'origine dati macchina o di file e fare clic su **OK**.  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **Avanzate**  
 **Impostazioni di rete:** specificare il **livello di rappresentazione** (il livello di rappresentazione che il server può essere utilizzato per rappresentare il client; corrisponde direttamente ai livelli di rappresentazione RPC) e **livello di protezione** (il livello di protezione dei dati inviati tra client e server; corrisponde direttamente a livelli di protezione RPC).  
  
 **Altro:** In **timeout connessione**, specificare il numero di secondi di inattività consentito prima che si verifichi un timeout. In **le autorizzazioni di accesso**, specificare le autorizzazioni di accesso per la connessione dati.  
  
     Per ulteriori informazioni sulle proprietà avanzate di inizializzazione, vedere la documentazione fornita con provider OLE DB specifico.  
  
 **All**  
     Questa scheda Visualizza un riepilogo delle proprietà di inizializzazione per l'origine dati e la connessione specificata. È possibile modificare questi valori.  
  
     Fare clic su **OK** alla fine. Il **Seleziona oggetto di Database** viene visualizzata la finestra di dialogo. Questa finestra di dialogo, selezionare la tabella, vista o stored procedure che verranno utilizzate dal consumer.  
  
 `Class`  
 Dopo aver selezionato un'origine dati, questa casella viene popolata con un nome di classe predefinito basato sulla tabella o stored procedure che è stato selezionato (vedere **selezionare un'origine dati** sotto). È possibile modificare il nome della classe.  
  
 **file con estensione h**  
 Dopo aver selezionato un'origine dati, questa casella viene popolata con un nome di classe intestazione predefinito basato sulla tabella o stored procedure che è stato selezionato (vedere **selezionare un'origine dati** sotto). È possibile modificare il nome del file di intestazione o selezionare un file di intestazione esistente.  
  
 **Con attributi**  
 Questa opzione specifica se la procedura guidata creerà classi consumer mediante gli attributi o le dichiarazioni di modello. Quando si seleziona questa opzione, la procedura guidata utilizza gli attributi invece di dichiarazioni di modello (si tratta dell'opzione predefinita). Quando si deseleziona questa opzione, la procedura guidata utilizza dichiarazioni di modello anziché gli attributi.  
  
-   Se si seleziona un consumer **tipo** della tabella, la procedura guidata utilizza il `db_source` e **db_table** attributi per creare la tabella e la funzione di accesso nella tabella delle dichiarazioni di classe e utilizza **db_column** per creare la mappa delle colonne, ad esempio:  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     anziché utilizzare la `CTable` classe modello per dichiarare la tabella e classe di tabella della funzione di accesso e le macro BEGIN_COLUMN_MAP ed END_COLUMN_MAP per creare la mappa delle colonne, ad esempio:  
  
 ``` 
 // Table accessor class  
    class COrdersAccessor; *// Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor>>;  
 ... 
 // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor) 
    COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)  
    COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)  
 ...  
    END_COLUMN_MAP() 
 ```  
  
-   Se si seleziona un consumer **tipo** del comando, la procedura guidata utilizza il `db_source` e **db_command** attributi e utilizza **db_column** per creare la mappa delle colonne, ad esempio:  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     anziché utilizzare il comando e le dichiarazioni di classe di comando della funzione di accesso nel file h della classe di comando, ad esempio:  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 Vedere [meccanismi fondamentali degli attributi](../../windows/basic-mechanics-of-attributes.md) per ulteriori informazioni.  
  
 **Type**  
 Selezionare uno di questi pulsanti di opzione per specificare se la classe consumer verrà derivata da `CTable` o `CCommand` (impostazione predefinita).  
  
 **tavolo**  
 Selezionare questa opzione se si desidera utilizzare `CTable` o **db_table** per creare la tabella e la funzione di accesso nella tabella delle dichiarazioni di classe.  
  
 **Comando**  
 Selezionare questa opzione se si desidera utilizzare `CCommand` o **db_command** per creare il comando e command accessor dichiarazioni di classe. Questa è la selezione predefinita.  
  
 **Supporto**  
 Selezionare le caselle di controllo per specificare i tipi di aggiornamento devono essere supportati nel consumer (il valore predefinito è none). Le seguenti imposterà [DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx) e le voci appropriate per [DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx) nel set di proprietà della mappa.  
  
 **Modifica**  
 Specifica che il consumer supporta gli aggiornamenti dei dati di riga nel set di righe.  
  
 **Inserimento**  
 Specifica che il consumer supporta l'inserimento di righe nel set di righe.  
  
 **Eliminazione**  
 Specifica che il consumer supporta l'eliminazione delle righe dal set di righe.  
  
## <a name="see-also"></a>Vedere anche  
 [Consumer OLE DB ATL](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [Aggiunta di funzionalità con creazioni guidate codice](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Stringhe di connessione e collegamenti dati (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)
