---
title: "Creazione guidata applicazione Win32 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.win32.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Creazione guidata applicazione Win32"
  - "Creazione guidata progetto Win32"
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Creazione guidata applicazione Win32
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La creazione guidata applicazione Win32 di Visual C\+\+ consente di creare uno dei quattro tipi di progetto \(elencati nell'intestazione della tabella seguente\). In ogni caso, è possibile specificare opzioni aggiuntive appropriate per il tipo di progetto aperto. La tabella seguente indica quali opzioni sono disponibili per ogni tipo di applicazione.  
  
|Tipo di supporto|Applicazione console|Applicazione \(Windows\) eseguibile|Libreria a collegamento dinamico|Libreria statica|  
|----------------------|--------------------------|-----------------------------------------|--------------------------------------|----------------------|  
|**Progetto vuoto**|Sì|Sì|Sì|No|  
|**Simboli di esportazione**|No|No|Sì|No|  
|**Intestazione precompilata**|No|No|No|Sì|  
|**Supporto ATL**|Sì|No|No|No|  
|**Supporto MFC**|Sì|No|No|Sì|  
  
## Panoramica  
 Questa pagina di procedura guidata illustra le impostazioni di progetto correnti per l'applicazione Win32 che si sta creando. Per impostazione predefinita, sono impostate le opzioni seguenti:  
  
-   Il progetto è un'applicazione Windows.  
  
-   Il progetto non è vuoto.  
  
-   Il progetto non contiene simboli di esportazione.  
  
-   Il progetto non usa un file di intestazione precompilata \(questa opzione è disponibile solo per progetti di libreria statica\).  
  
-   Il progetto non include supporto né per MFC né per ATL.  
  
 Per modificare questi valori predefiniti, fare clic sulla scheda [Impostazioni applicazione](../windows/application-settings-win-32-project-wizard.md) nella colonna sinistra della procedura guidata e apportare le modifiche desiderate.  
  
 Dopo aver creato un'applicazione desktop di Windows, è possibile aggiungere classi C\+\+ generiche usando la procedura guidata per codice[generico](../ide/generic-cpp-class-wizard.md). È possibile aggiungere altri elementi, quali file HTML, file di intestazione, risorse o file di testo.  
  
> [!NOTE]
>  Non è possibile aggiungere classi ATL ed è possibile aggiungere classi MFC solo a quei tipi di applicazioni desktop di Windows che supportano MFC \(vedere la tabella precedente\).  
  
 È possibile visualizzare i file creati per il progetto con la procedura guidata in **Esplora soluzioni**. Per altre informazioni sui file creati per il progetto con la procedura guidata, vedere il file ReadMe.txt generato dal progetto. Per altre informazioni sui tipi di file, vedere [Tipi di file creati per i progetti di Visual C\+\+](../ide/file-types-created-for-visual-cpp-projects.md).  
  
## Vedere anche  
 [Creazione di un'applicazione desktop di Windows vuota](../windows/creating-an-empty-windows-desktop-application.md)   
 [Tipi di progetto Visual C\+\+](../ide/visual-cpp-project-types.md)