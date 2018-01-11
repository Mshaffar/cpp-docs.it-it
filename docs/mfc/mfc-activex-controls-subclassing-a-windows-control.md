---
title: 'Controlli ActiveX MFC: Creazione di sottoclassi di un controllo di Windows | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- precreatewindow
- IsSubclassed
dev_langs: C++
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3e41eefdf1c1be2d0e91061e0efce5f5408c1848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Controlli ActiveX MFC: creazione di una sottoclasse per un controllo Windows
In questo articolo viene descritto il processo per la creazione di una sottoclasse di un controllo Windows comune per creare un controllo ActiveX. La creazione di una sottoclasse di un controllo Windows esistente è un modo rapido per sviluppare un controllo ActiveX. Il nuovo controllo disporrà delle funzionalità dei controlli Windows sottoclassati, come il disegno e la risposta ai clic del mouse. Esempio dei controlli ActiveX MFC [pulsante](../visual-cpp-samples.md) è un esempio di creazione di sottoclassi di un controllo di Windows.  
  
 Per creare una sottoclasse di un controllo Windows, completare le seguenti attività:  
  
-   [Eseguire l'override di funzioni membro PreCreateWindow e IsSubclassedControl di COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [Modificare la funzione membro OnDraw](#_core_modifying_the_ondraw_member_function)  
  
-   [Gestire eventuali messaggi di controllo ActiveX (OCM) applicati al controllo](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  Maggior parte di queste operazioni viene eseguita automaticamente dalla creazione guidata controllo ActiveX se si seleziona il controllo da sottoclassare il **Seleziona classe finestra padre** elenco a discesa nel **le impostazioni di controllo** pagina.  
  
 Per ulteriori informazioni sulla creazione di una sottoclasse di un controllo, vedere l'articolo della Knowledge Base Q243454.  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Override di IsSubclassedControl e PreCreateWindow  
 Per eseguire l'override di `PreCreateWindow` e `IsSubclassedControl`, aggiungere le seguenti righe di codice alla sezione `protected` della dichiarazione della classe del controllo:  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 Nel file di implementazione del controllo (.CPP), aggiungere le seguenti righe di codice per implementare le due funzioni sottoposte a override:  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 Notare che, in questo esempio, il controllo pulsante Windows viene specificato in `PreCreateWindow`. Tuttavia, tutti i controlli Windows standard possono essere sottoclassati. Per ulteriori informazioni sui controlli Windows standard, vedere [controlli](../mfc/controls-mfc.md).  
  
 Quando si crea una sottoclasse di un controllo di Windows, si desidera specificare lo stile di finestra particolare (**WS _**) o lo stile di finestra esteso (**WS_EX _**) flag per essere utilizzata per creare la finestra del controllo. È possibile impostare i valori per questi parametri, il `PreCreateWindow` funzione membro modificando il **cs** e **dwExStyle** campi della struttura. Le modifiche apportate a questi campi devono essere apportate mediante un'operazione `OR`, per conservare i flag predefiniti impostati dalla classe `COleControl`. Ad esempio, se il controllo crea una sottoclasse del controllo BUTTON e si desidera che il controllo venga visualizzato come casella di controllo, inserire la seguente riga di codice nell'implementazione di `CSampleCtrl::PreCreateWindow`, prima dell'istruzione return:  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 Questa operazione aggiunge il **BS_CHECKBOX** , flag di stile, lasciando al contempo il flag di stile predefinito (**WS_CHILD**) della classe `COleControl` intatto.  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a>Modifica la funzione membro OnDraw  
 Se si desidera che il controllo sottoclassato mantenga lo stesso aspetto del controllo Windows corrispondente, la funzione membro `OnDraw` per il controllo deve contenere solo una chiamata alla funzione membro `DoSuperclassPaint`, come mostrato nel seguente esempio:  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 La funzione membro `DoSuperclassPaint`, implementata da `COleControl`, utilizza la procedura della finestra del controllo Windows per disegnare il controllo nel contesto di dispositivo specificato, all'interno del rettangolo di delimitazione. In questo modo il controllo è visibile anche quando non è attivo.  
  
> [!NOTE]
>  Il `DoSuperclassPaint` funziona solo con i tipi di controllo che consentono a un contesto di dispositivo deve essere passato come funzione membro di **wParam** di un `WM_PAINT` messaggio. Ciò include alcuni dei controlli Windows standard, ad esempio **barra di scorrimento** e **pulsante**e tutti i controlli comuni. Per i controlli che non supportano questo comportamento, è necessario fornire il proprio codice per visualizzare correttamente un controllo inattivo.  
  
##  <a name="_core_handling_reflected_window_messages"></a>Gestione dei messaggi finestra riflessi  
 I controlli Windows in genere inviano determinati messaggi finestra alla rispettiva finestra padre. Alcuni di questi messaggi, ad esempio **WM_COMMAND**, fornire la notifica di un'azione dell'utente. Altri, come `WM_CTLCOLOR`, vengono utilizzati per ottenere informazioni dalla finestra padre. Un controllo ActiveX in genere comunica con la finestra padre in altri modi. Le notifiche vengono passate generando eventi (inviando notifiche di eventi) e le informazioni sul contenitore del controllo vengono ottenute accedendo alle proprietà di ambiente del contenitore. Grazie a queste tecniche di comunicazione, i contenitori di controlli ActiveX non prevedono l'elaborazione dei messaggi finestra inviati dal controllo.  
  
 Per impedire al contenitore di ricevere dei messaggi finestra inviati da un controllo Windows sottoclassato, `COleControl` crea una finestra aggiuntiva che serve da padre del controllo. Questa finestra aggiuntiva, denominata "riflettore", viene creata solo per un controllo ActiveX che crea la sottoclasse di un controllo Windows e dispone delle stesse dimensioni e posizione della finestra del controllo. La finestra riflettore intercetta determinati messaggi della finestra e li invia al controllo. Il controllo, nella routine della finestra, può quindi elaborare questi messaggi riflessi intraprendendo le opportune azioni per un controllo ActiveX (ad esempio, generando un evento). Vedere [ID di messaggi finestra riflessi](../mfc/reflected-window-message-ids.md) per un elenco di finestre intercettati i messaggi e i relativi messaggi riflessi.  
  
 Un contenitore di controlli ActiveX può essere progettato per eseguire la reflection dei messaggi, evitando a `COleControl` la necessità di creare la finestra riflettore e riducendo il sovraccarico di runtime per un controllo Windows sottoclassato. `COleControl`rileva se il contenitore supporta questa funzionalità verificando per un ambiente MessageReflect con un valore di **TRUE**.  
  
 Per gestire un messaggio della finestra riflesso, aggiungere una voce alla mappa messaggi del controllo e implementare una funzione del gestore. Poiché i messaggi riflessi non fanno parte del set di messaggi standard definiti da Windows, Visualizzazione classi non supporta l'aggiunta di tali gestori di messaggi. Tuttavia, non è difficile aggiungere un gestore manualmente.  
  
 Per aggiungere manualmente un gestore messaggi per un messaggio della finestra riflesso, effettuare le operazioni seguenti:  
  
-   Nel file .H della classe del controllo, dichiarare una funzione del gestore. La funzione deve avere un tipo restituito di **LRESULT** e due parametri, con tipi **WPARAM** e **LPARAM**, rispettivamente. Ad esempio:  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   Nel file .CPP della classe del controllo, aggiungere una voce `ON_MESSAGE` alla mappa messaggi. I parametri di questa voce devono essere l'identificatore del messaggio e il nome della funzione del gestore. Ad esempio:  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   Anche nel. I file CPP, implementare il **OnOcmCommand** funzione membro per elaborare il messaggio riflesso. Il **wParam** e **lParam** i parametri sono identici a quelli del messaggio originale della finestra.  
  
 Per un esempio di reflection di elaborazione dei messaggi, vedere l'esempio di controlli ActiveX MFC [pulsante](../visual-cpp-samples.md). Viene illustrato un **OnOcmCommand** gestore che rileva il **BN_CLICKED** codice di notifica e risponde generando (inviando) un evento Click.  
  
## <a name="see-also"></a>Vedere anche  
 [Controlli ActiveX MFC](../mfc/mfc-activex-controls.md)
