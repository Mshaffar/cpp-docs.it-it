---
title: Classe CPrintDialog | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
dev_langs: C++
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 653cdc4580862288d98600603c1b45526ea38675
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="cprintdialog-class"></a>Classe CPrintDialog
Incapsula i servizi forniti dalla finestra di dialogo comune di Windows per la stampa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CPrintDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CPrintDialog::CPrintDialog](#cprintdialog)|Costruisce un oggetto `CPrintDialog`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Crea un contesto di dispositivo stampante senza visualizzare la finestra di dialogo Stampa.|  
|[CPrintDialog::DoModal](#domodal)|Visualizza la finestra di dialogo e consente all'utente di effettuare una selezione.|  
|[CPrintDialog::GetCopies](#getcopies)|Recupera il numero di copie richieste.|  
|[CPrintDialog::GetDefaults](#getdefaults)|Recupera impostazioni predefinite del dispositivo senza visualizzare una finestra di dialogo.|  
|[CPrintDialog::GetDeviceName](#getdevicename)|Recupera il nome del dispositivo stampante selezionata.|  
|[CPrintDialog::GetDevMode](#getdevmode)|Recupera il `DEVMODE` struttura.|  
|[CPrintDialog::GetDriverName](#getdrivername)|Recupera il nome del driver della stampante selezionata.|  
|[CPrintDialog::GetFromPage](#getfrompage)|Recupera la pagina iniziale dell'intervallo di stampa.|  
|[CPrintDialog::GetPortName](#getportname)|Recupera il nome della porta di stampante selezionata.|  
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Recupera un handle per il contesto di dispositivo stampante.|  
|[CPrintDialog::GetToPage](#gettopage)|Recupera la pagina finale dell'intervallo di stampa.|  
|[CPrintDialog::PrintAll](#printall)|Determina se stampare tutte le pagine del documento.|  
|[CPrintDialog::PrintCollate](#printcollate)|Determina se confrontati copie sono richiesti.|  
|[CPrintDialog::PrintRange](#printrange)|Determina se stampare solo un intervallo di pagine specificato.|  
|[CPrintDialog::PrintSelection](#printselection)|Determina se stampare solo gli elementi attualmente selezionati.|  
  
### <a name="public-data-members"></a>Membri dati pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CPrintDialog:: M_pd](#m_pd)|Una struttura utilizzata per personalizzare un `CPrintDialog` oggetto.|  
  
## <a name="remarks"></a>Note  
 Finestre di dialogo Stampa comuni forniscono un modo semplice per implementare le finestre di dialogo di stampa e stampare il programma di installazione in modo coerente con gli standard di Windows.  
  
> [!NOTE]
>  La `CPrintDialogEx` classe incapsula i servizi forniti dalla finestra delle proprietà di stampa di Windows 2000. Per ulteriori informazioni, vedere il [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) Panoramica.  
  
 `CPrintDialog`della funzionalità è stata sostituita da quella di [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), progettato per fornire una finestra di dialogo comune per entrambi il programma di installazione e impostazione della pagina di stampa.  
  
 È possibile basarsi su framework per gestire molti aspetti del processo di stampa per l'applicazione. In questo caso, il framework visualizza automaticamente nella finestra di dialogo comune per la stampa. Anche avere l'handle del framework stampa per l'applicazione è possibile eseguire l'override di finestra di dialogo Stampa comune con la propria finestra di dialogo Stampa. Per ulteriori informazioni sull'utilizzo di framework per gestire le attività di stampa, vedere l'articolo [stampa](../../mfc/printing.md).  
  
 Se si desidera l'applicazione per gestire la stampa senza coinvolgere del framework, è possibile utilizzare il `CPrintDialog` con il costruttore fornito "così com'è", oppure è possibile derivare la propria classe di finestra di dialogo da `CPrintDialog` e scrivere un costruttore in base alle esigenze. In entrambi i casi, queste finestre di dialogo si comportano come finestre di dialogo MFC standard perché vengono derivati dalla classe `CCommonDialog`.  
  
 Per utilizzare un `CPrintDialog` oggetto, creare innanzitutto l'oggetto utilizzando il `CPrintDialog` costruttore. Una volta la finestra di dialogo è stata creata, è possibile impostare o modificare i valori di [m_pd](#m_pd) struttura per inizializzare i valori dei controlli della finestra di dialogo. Il `m_pd` struttura è di tipo [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843). Per ulteriori informazioni su tale struttura, vedi il Windows SDK.  
  
 Se non si fornisce i proprio handle `m_pd` per il **hDevMode** e **hDevNames** membri, assicurarsi di chiamare la funzione Windows **GlobalFree** per i punti di controllo al termine con la finestra di dialogo. Quando si utilizza l'implementazione di impostazioni di stampa del framework fornito da `CWinApp::OnFilePrintSetup`, non è necessario liberare gli handle. Gli handle vengono mantenuti dal `CWinApp` e vengono liberati `CWinApp`del distruttore. È necessario liberare gli handle quando si utilizza solo `CPrintDialog` autonomo.  
  
 Dopo l'inizializzazione di controlli di finestra di dialogo, chiamare il `DoModal` funzione membro per visualizzare la finestra di dialogo e consentire all'utente di selezionare le opzioni di stampa. `DoModal`indica se l'utente selezionato OK ( **IDOK**) o annullare ( **IDCANCEL**) pulsante.  
  
 Se `DoModal` restituisce **IDOK**, è possibile utilizzare uno dei `CPrintDialog`di funzioni membro per recuperare le informazioni di input dall'utente.  
  
 Il `CPrintDialog::GetDefaults` membro funzione è utile per recuperare le impostazioni predefinite della stampante senza visualizzare una finestra di dialogo. Questa funzione membro senza intervento dell'utente.  
  
 È possibile utilizzare le finestre **CommDlgExtendedError** funzione per determinare se si è verificato un errore durante l'inizializzazione della finestra di dialogo e per ulteriori informazioni sull'errore. Per ulteriori informazioni su questa funzione, vedi il Windows SDK.  
  
 `CPrintDialog`si basa sul COMMDLG. File DLL che viene fornito con Windows 3.1 e versioni successive.  
  
 Per personalizzare la finestra di dialogo, derivare una classe da `CPrintDialog`, fornire un modello di finestra di dialogo personalizzata e aggiungere una mappa messaggi per elaborare i messaggi di notifica da controlli estesi. Eventuali messaggi non elaborati devono essere passati alla classe di base. La funzione hook di personalizzazione non è necessaria.  
  
 Per elaborare lo stesso messaggio in modo diverso a seconda se la finestra di dialogo Stampa o l'installazione di stampa, è necessario derivare una classe per ogni finestra di dialogo. È inoltre necessario eseguire l'override di Windows **AttachOnSetup** (funzione), che gestisce la creazione di una nuova finestra di dialogo quando viene selezionato il pulsante di stampa il programma di installazione all'interno di una finestra di dialogo di stampa.  
  
 Per ulteriori informazioni sull'utilizzo `CPrintDialog`, vedere [classi di finestre di dialogo comuni](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxdlgs. h  
  
##  <a name="cprintdialog"></a>CPrintDialog::CPrintDialog  
 Costruisce l'oggetto finestra di dialogo di stampa di Windows o l'installazione di stampa.  
  
```  
CPrintDialog(
    BOOL bPrintSetupOnly,  
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametri  
 `bPrintSetupOnly`  
 Specifica se viene visualizzata la finestra di dialogo Impostazioni di stampa o la finestra di dialogo di stampa di Windows standard. Impostare questo parametro su **TRUE** per visualizzare la finestra di dialogo Impostazioni di stampa di Windows standard. Impostarla su **FALSE** per visualizzare la finestra di dialogo di stampa Windows. Se `bPrintSetupOnly` è **FALSE**, un pulsante di opzione Imposta stampante viene ancora visualizzato nella finestra di dialogo Stampa.  
  
 `dwFlags`  
 Uno o più flag che è possibile utilizzare per personalizzare le impostazioni nella finestra di dialogo, combinati utilizzando l'operatore OR bit per bit. Ad esempio, il **PD_ALLPAGES** flag imposta l'intervallo di stampa predefinite per tutte le pagine del documento. Vedere il [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struttura in Windows SDK per ulteriori informazioni su questi flag.  
  
 `pParentWnd`  
 Puntatore alla finestra padre o proprietaria della finestra di dialogo.  
  
### <a name="remarks"></a>Note  
 Questa funzione membro solo costruisce l'oggetto. Utilizzare il `DoModal` funzione membro per visualizzare la finestra di dialogo.  
  
 Si noti che quando si chiama il costruttore con `bPrintSetupOnly` impostato su **FALSE**, **PD_RETURNDC** flag viene utilizzato automaticamente. Dopo la chiamata `DoModal`, `GetDefaults`, o `GetPrinterDC`, verrà restituita una controller di dominio della stampante `m_pd.hDC`. Il controller di dominio deve essere liberata con una chiamata a [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) dal chiamante di `CPrintDialog`.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC  
 Crea un contesto di dispositivo stampante (DC) dal [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) e [DEVNAMES](../../mfc/reference/devnames-structure.md) strutture.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Valore restituito  
 Handle per il contesto di dispositivo stampante appena creato.  
  
### <a name="remarks"></a>Note  
 Si presuppone che il controller di dominio sia la stampante corrente controller di dominio e qualsiasi altro ottenuto in precedenza stampante che i controller di dominio devono essere eliminati dall'utente. Questa funzione può essere chiamata e il controller di dominio risultante utilizzato, senza visualizzare mai la finestra di dialogo Stampa.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]  
  
##  <a name="domodal"></a>CPrintDialog::DoModal  
 Consente di visualizzare la finestra di dialogo Stampa comune Windows e consente all'utente di selezionare varie opzioni di stampare, ad esempio il numero di copie, intervallo di pagine, e se devono essere collazionate copie.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Valore restituito  
 **IDOK** o **IDCANCEL**. Se **IDCANCEL** viene restituito, chiamare il Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funzione per determinare se si è verificato un errore.  
  
 **IDOK** e **IDCANCEL** sono le costanti che indicano se l'utente ha selezionato il pulsante OK o Annulla.  
  
### <a name="remarks"></a>Note  
 Se si desidera inizializzare le varie opzioni della finestra di dialogo Stampa impostando i membri del `m_pd` struttura, è consigliabile farlo prima di chiamare `DoModal`, ma dopo che l'oggetto finestra di dialogo.  
  
 Dopo la chiamata `DoModal`, è possibile chiamare le funzioni per recuperare le impostazioni o input informazioni dall'utente nella finestra di dialogo altri membri.  
  
 Si noti che quando si chiama il costruttore con `bPrintSetupOnly` impostato su **FALSE**, **PD_RETURNDC** flag viene utilizzato automaticamente. Dopo la chiamata `DoModal`, `GetDefaults`, o `GetPrinterDC`, verrà restituita una controller di dominio della stampante `m_pd.hDC`. Il controller di dominio deve essere liberata con una chiamata a [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) dal chiamante di `CPrintDialog`.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog::CreatePrinterDC](#createprinterdc).  
  
##  <a name="getcopies"></a>CPrintDialog::GetCopies  
 Recupera il numero di copie richieste.  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di copie richieste.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata `DoModal` per recuperare il numero di copie richieste.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdefaults"></a>CPrintDialog::GetDefaults  
 Recupera le impostazioni predefinite del dispositivo della stampante predefinita senza visualizzare una finestra di dialogo.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se la funzione ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 I valori recuperati sono inseriti nel `m_pd` struttura.  
  
 In alcuni casi, una chiamata a questa funzione chiamerà il [costruttore](#cprintdialog) per `CPrintDialog` con `bPrintSetupOnly` impostato su **FALSE**. In questi casi, una stampante e **hDevNames** e **hDevMode** (due punti di controllo si trova nel `m_pd` membro dati) vengono allocate automaticamente.  
  
 Se il costruttore per `CPrintDialog` è stata chiamata con `bPrintSetupOnly` impostato su **FALSE**, questa funzione non verrà restituito solo **hDevNames** e **hDevMode** (che si trova **m_pd.hDevNames** e **m_pd.hDevMode**) al chiamante, ma restituirà anche una stampante in **m_pd.hDC**. È responsabilità del chiamante per eliminare la stampante e chiamare Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) funzione su handle quando si è concluso il `CPrintDialog` oggetto.  
  
### <a name="example"></a>Esempio  
 Questo frammento di codice ottiene il contesto di dispositivo della stampante predefinita e segnala all'utente la risoluzione della stampante in punti per pollice. (L'attributo di funzionalità della stampante è noto anche come DPI.)  
  
 [!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]  
  
##  <a name="getdevicename"></a>CPrintDialog::GetDeviceName  
 Recupera il nome del dispositivo stampante selezionata.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il nome della stampante attualmente selezionata.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata [DoModal](#domodal) per recuperare il nome della stampante attualmente selezionata o dopo la chiamata [GetDefaults](#getdefaults) per recuperare le impostazioni predefinite del dispositivo corrente della stampante predefinita. Utilizzare un puntatore al `CString` oggetto restituito da `GetDeviceName` come valore di `lpszDeviceName` in una chiamata a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Esempio  
 Questo frammento di codice mostra il nome dell'utente predefinito della stampante e la porta che è connessa, insieme al nome di spooler usato dalla stampante. Il codice potrebbe visualizzare una finestra di messaggio con la dicitura "stampante predefinita è HP LaserJet IIIP \\\server\share utilizzando winspool.", ad esempio.  
  
 [!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]  
  
##  <a name="getdevmode"></a>CPrintDialog::GetDevMode  
 Recupera il `DEVMODE` struttura.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struttura dei dati, che contiene informazioni sull'inizializzazione di dispositivo e l'ambiente di un driver di stampato. È necessario sbloccare la memoria utilizzata da questa struttura con Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funzione, come descritto in Windows SDK.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata [DoModal](#domodal) o [GetDefaults](#getdefaults) per recuperare le informazioni relative al dispositivo di stampa.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdrivername"></a>CPrintDialog::GetDriverName  
 Recupera il nome del driver della stampante selezionata.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto `CString` specificando il nome del driver definiti dal sistema.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata [DoModal](#domodal) o [GetDefaults](#getdefaults) per recuperare il nome del driver di dispositivo stampante definita dal sistema. Utilizzare un puntatore al `CString` oggetto restituito da `GetDriverName` come valore di `lpszDriverName` in una chiamata a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getfrompage"></a>CPrintDialog::GetFromPage  
 Recupera la pagina iniziale dell'intervallo di stampa.  
  
```  
int GetFromPage() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Numero di pagina iniziale dell'intervallo di pagine da stampare.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata `DoModal` per recuperare il numero di pagina iniziale dell'intervallo di pagine da stampare.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog:: M_pd](#m_pd).  
  
##  <a name="getportname"></a>CPrintDialog::GetPortName  
 Recupera il nome della porta di stampante selezionata.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il nome della porta di stampante selezionata.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata [DoModal](#domodal) o [GetDefaults](#getdefaults) per recuperare il nome della porta di stampante selezionata.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getprinterdc"></a>CPrintDialog::GetPrinterDC  
 Recupera un handle per il contesto di dispositivo stampante.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Un handle per il contesto di dispositivo stampante se ha esito positivo. in caso contrario **NULL**.  
  
### <a name="remarks"></a>Note  
 Se il `bPrintSetupOnly` parametro il `CPrintDialog` costruttore è stato **FALSE** (che indica che viene visualizzata la finestra di dialogo di stampa), quindi `GetPrinterDC` restituisce un handle per il contesto di dispositivo stampante. È necessario chiamare Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) funzione per eliminare il contesto di dispositivo al termine utilizzarlo.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]  
  
##  <a name="gettopage"></a>CPrintDialog::GetToPage  
 Recupera la pagina finale dell'intervallo di stampa.  
  
```  
int GetToPage() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Numero di pagina finale dell'intervallo di pagine da stampare.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata `DoModal` per recuperare il numero di pagina finale dell'intervallo di pagine da stampare.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog:: M_pd](#m_pd).  
  
##  <a name="m_pd"></a>CPrintDialog:: M_pd  
 Struttura i cui membri archiviano le caratteristiche dell'oggetto finestra di dialogo.  
  
```  
PRINTDLG& m_pd;  
```  
  
### <a name="remarks"></a>Note  
 Al termine della creazione un `CPrintDialog` dell'oggetto, è possibile utilizzare `m_pd` per impostare i vari aspetti della finestra di dialogo prima di chiamare il [DoModal](#domodal) funzione membro. Per ulteriori informazioni sul `m_pd` struttura, vedere [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) in Windows SDK.  
  
 Se si modifica il `m_pd` (membro dati) direttamente, si eseguirà l'override di alcun comportamento predefinito.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]  
  
##  <a name="printall"></a>CPrintDialog::PrintAll  
 Determina se stampare tutte le pagine del documento.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se tutte le pagine del documento da stampare; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata `DoModal` per determinare se stampare tutte le pagine del documento.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog:: M_pd](#m_pd).  
  
##  <a name="printcollate"></a>CPrintDialog::PrintCollate  
 Determina se confrontati copie sono richiesti.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se l'utente seleziona la casella di controllo collate nella finestra di dialogo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata `DoModal` per determinare se la stampante deve collate stampate tutte le copie del documento.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]  
  
##  <a name="printrange"></a>CPrintDialog::PrintRange  
 Determina se stampare solo un intervallo di pagine specificato.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se solo un intervallo di pagine del documento devono essere visualizzate; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata `DoModal` per determinare se visualizzare solo un intervallo di pagine del documento.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog:: M_pd](#m_pd).  
  
##  <a name="printselection"></a>CPrintDialog::PrintSelection  
 Determina se stampare solo gli elementi attualmente selezionati.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se solo gli elementi selezionati devono essere visualizzate; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione dopo la chiamata `DoModal` per determinare se visualizzare solo gli elementi attualmente selezionati.  
  
### <a name="example"></a>Esempio  
  Per vedere l'esempio [CPrintDialog:: M_pd](#m_pd).  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio MFC viene](../../visual-cpp-samples.md)   
 [Classe CCommonDialog](../../mfc/reference/ccommondialog-class.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Struttura CPrintInfo](../../mfc/reference/cprintinfo-structure.md)