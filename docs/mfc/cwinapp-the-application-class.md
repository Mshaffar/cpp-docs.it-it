---
title: 'CWinApp: Classe Application | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1f146df2dd4f97affdaf1c3107d1b00bfd86876
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="cwinapp-the-application-class"></a>CWinApp: classe Application
La classe principale dell'applicazione in MFC incapsula l'inizializzazione, in esecuzione e la chiusura di un'applicazione per il sistema operativo Windows. Un'applicazione compilata nel framework deve avere uno e un solo oggetto di una classe derivata da [CWinApp](../mfc/reference/cwinapp-class.md). Questo oggetto viene costruito prima della creazione di windows.  
  
 `CWinApp`derivato da `CWinThread`, che rappresenta il thread principale di esecuzione per l'applicazione, che potrebbe avere uno o più thread. Nelle versioni recenti di MFC, la `InitInstance`, **eseguire**, `ExitInstance`, e `OnIdle` funzioni membro si trovano nella classe `CWinThread`. Queste funzioni sono descritte di seguito come se fossero `CWinApp` membri, invece, perché la discussione riguarda il ruolo dell'oggetto come oggetto applicazione anziché come thread principale.  
  
> [!NOTE]
>  La classe dell'applicazione costituisce il thread dell'applicazione principale di esecuzione. Utilizzare le funzioni API Win32, è possibile creare anche secondario thread di esecuzione. Questi thread è possono utilizzare la libreria MFC. Per ulteriori informazioni, vedere [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Come con qualsiasi programma per il sistema operativo Windows, l'applicazione framework dispone di un `WinMain` (funzione). In un'applicazione di framework, tuttavia, non si scrive `WinMain`. Viene fornito dalla libreria di classi e viene chiamato quando l'avvio dell'applicazione. `WinMain`esegue i servizi standard, ad esempio la registrazione di classi di finestra. Quindi chiama le funzioni membro dell'oggetto application per inizializzare l'applicazione ed eseguirla. (È possibile personalizzare `WinMain` eseguendo l'override di `CWinApp` le funzioni membro che `WinMain` chiamate.)  
  
 Per inizializzare l'applicazione, `WinMain` chiama l'oggetto di applicazione `InitApplication` e `InitInstance` funzioni membro. Per eseguire il ciclo di messaggi dell'applicazione, `WinMain` chiamate di **eseguire** funzione membro. Al termine, `WinMain` chiama l'oggetto di applicazione `ExitInstance` funzione membro.  
  
> [!NOTE]
>  I nomi visualizzati **grassetto** in questa documentazione indicano gli elementi disponibili per la libreria Microsoft Foundation Class e Visual C++. Nomi riportati nella `monospaced` tipo indicano gli elementi che si crea o si esegue l'override.  
  
## <a name="see-also"></a>Vedere anche  
 [Argomenti MFC generali](../mfc/general-mfc-topics.md)   
 [CWinApp e la creazione guidata applicazione MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [Funzioni membro CWinApp sottoponibili a override](../mfc/overridable-cwinapp-member-functions.md)   
 [Servizi CWinApp speciali](../mfc/special-cwinapp-services.md)
