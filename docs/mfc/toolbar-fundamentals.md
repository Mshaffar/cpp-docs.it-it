---
title: Nozioni fondamentali sulla barra degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RT_TOOLBAR
dev_langs: C++
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 136b9f5dd36c9e4092b8e5c15ac1738541cf71f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="toolbar-fundamentals"></a>Nozioni fondamentali sulla barra degli strumenti
In questo articolo vengono descritte l'implementazione MFC fondamentale che consente di aggiungere una barra degli strumenti predefinita per l'applicazione selezionando un'opzione nella creazione guidata applicazione. Gli argomenti trattati includono:  
  
-   [L'opzione della barra degli strumenti di creazione guidata applicazione](#_core_the_appwizard_toolbar_option)  
  
-   [Barra degli strumenti nel codice](#_core_the_toolbar_in_code)  
  
-   [La modifica della risorsa barra degli strumenti](#_core_editing_the_toolbar_resource)  
  
-   [Più barre degli strumenti](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a>L'opzione della barra degli strumenti dell'applicazione guidata  
 Per ottenere una singola barra degli strumenti con pulsanti predefiniti, selezionare l'opzione della barra degli strumenti Standard di ancoraggio della pagina di funzionalità interfaccia utente. Consente di aggiungere codice all'applicazione che:  
  
-   Crea l'oggetto della barra degli strumenti.  
  
-   Gestisce la barra degli strumenti, inclusa la possibilità per ancorare o mobile.  
  
##  <a name="_core_the_toolbar_in_code"></a>Barra degli strumenti nel codice  
 La barra degli strumenti è un [CToolBar](../mfc/reference/ctoolbar-class.md) oggetto dichiarato come un membro di dati dell'applicazione **CMainFrame** classe. In altre parole, l'oggetto della barra degli strumenti è incorporato nell'oggetto finestra cornice principale. Ciò significa che MFC crea la barra degli strumenti quando crea la finestra cornice ed elimina la barra degli strumenti quando elimina la finestra cornice. Nella seguente dichiarazione di classe parziale, per un'applicazione MDI (interfaccia) di documenti multipli, Mostra i membri dati per una barra degli strumenti incorporata e una barra di stato incorporata. Viene inoltre l'override del `OnCreate` funzione membro.  
  
 [!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]  
  
 La barra degli strumenti si verifica **CMainFrame:: OnCreate**. MFC chiama [OnCreate](../mfc/reference/cwnd-class.md#oncreate) dopo la creazione della finestra per il frame ma prima che diventi visibile. Il valore predefinito `OnCreate` che genera la creazione guidata applicazione vengono eseguite le attività della barra degli strumenti seguenti:  
  
1.  Chiamate di `CToolBar` dell'oggetto [crea](../mfc/reference/ctoolbar-class.md#create) funzione membro per creare l'oggetto sottostante [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) oggetto.  
  
2.  Chiamate [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) per caricare le informazioni della risorsa barra degli strumenti.  
  
3.  Chiama le funzioni per consentire di ancoraggio, a virgola mobile e descrizioni comandi. Per informazioni dettagliate su queste chiamate, vedere l'articolo [ancorate e mobili barre degli strumenti](../mfc/docking-and-floating-toolbars.md).  
  
> [!NOTE]
>  L'esempio MFC generale [DOCKTOOL](../visual-cpp-samples.md) sono incluse immagini delle barre degli strumenti MFC sia vecchi che nuovi. Le barre degli strumenti che usano **COldToolbar** richiedono chiamate nel passaggio 2 per `LoadBitmap` (anziché `LoadToolBar`) e a `SetButtons`. Le nuove barre degli strumenti richiedono chiamate a `LoadToolBar`.  
  
 L'ancoraggio, a virgola mobile e chiamate di strumento suggerimenti sono facoltative. È possibile rimuovere le righe da `OnCreate` se si preferisce. Il risultato è una barra degli strumenti che rimane fisso, non è possibile float o ancorata e non è possibile visualizzare le descrizioni comandi.  
  
##  <a name="_core_editing_the_toolbar_resource"></a>La modifica della risorsa barra degli strumenti  
 La barra degli strumenti predefinita con la creazione guidata applicazioni è basato su un **RT_TOOLBAR** risorsa personalizzata, introdotto nella versione 4.0 di MFC. È possibile modificare questa risorsa con il [editor barra degli strumenti](../windows/toolbar-editor.md). L'editor consente di aggiungere, eliminare e riordinare i pulsanti. Contiene un editor grafico per i pulsanti che sono molto simili all'editor di immagini generali in Visual C++. Se le barre degli strumenti nelle versioni precedenti di Visual C++ è stato modificato, è disponibile l'attività molto più semplice a questo punto.  
  
 Per connettere un comando di un pulsante della barra degli strumenti, assegnare al pulsante un ID di comando, ad esempio `ID_MYCOMMAND`. Specificare l'ID di comando nella pagina delle proprietà del pulsante nell'editor barra degli strumenti. Creare quindi una funzione del gestore per il comando (vedere [Mapping di messaggi a funzioni](../mfc/reference/mapping-messages-to-functions.md) per altre informazioni).  
  
 Nuovo [CToolBar](../mfc/reference/ctoolbar-class.md) funzioni membro con il **RT_TOOLBAR** risorse. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) ora prende il posto di [LoadBitmap](../mfc/reference/ctoolbar-class.md#loadbitmap) per caricare la bitmap delle immagini dei pulsanti della barra degli strumenti, e [SetButtons](../mfc/reference/ctoolbar-class.md#setbuttons) per impostare gli stili dei pulsanti e connettere i pulsanti con le immagini bitmap.  
  
 Per informazioni dettagliate sull'utilizzo dell'editor barra degli strumenti, vedere [Editor barra degli strumenti](../windows/toolbar-editor.md).  
  
##  <a name="_core_multiple_toolbars"></a>Più barre degli strumenti  
 La creazione guidata applicazione fornisce sulla barra degli strumenti di un valore predefinito. Se è necessario più di una barra degli strumenti dell'applicazione, è possibile modellare il codice per le barre degli strumenti aggiuntivi in base al codice generato dalla procedura guidata per la barra degli strumenti predefinita.  
  
 Se si desidera visualizzare una barra degli strumenti come il risultato di un comando, è necessario:  
  
-   Creare una nuova risorsa barra degli strumenti con la barra degli strumenti dell'editor e caricarla in `OnCreate` con il [LoadToolbar](../mfc/reference/ctoolbar-class.md#loadtoolbar) funzione membro.  
  
-   Incorporare un nuovo [CToolBar](../mfc/reference/ctoolbar-class.md) oggetto nella classe della finestra cornice principale.  
  
-   Assicurarsi che chiama la funzione appropriata in `OnCreate` per ancorare o rendere mobile la barra degli strumenti, impostare gli stili e così via.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Ciò che si desidera saperne di più  
  
-   [Implementazione della barra degli strumenti MFC (informazioni generali sulle barre degli strumenti)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Ancoraggio e barre degli strumenti mobili](../mfc/docking-and-floating-toolbars.md)  
  
-   [Descrizione comandi](../mfc/toolbar-tool-tips.md)  
  
-   Il [CToolBar](../mfc/reference/ctoolbar-class.md) e [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) classi  
  
-   [Utilizzo del controllo barra degli strumenti](../mfc/working-with-the-toolbar-control.md)  
  
-   [Utilizzo delle barre degli strumenti precedente](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione della barra degli strumenti MFC](../mfc/mfc-toolbar-implementation.md)
