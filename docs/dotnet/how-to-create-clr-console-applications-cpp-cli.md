---
title: "Procedura: Creare applicazioni console CLR (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "applicazioni console, modelli"
  - "applicazioni console CLR, modello di progetto"
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: Creare applicazioni console CLR (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

È possibile usare il modello di applicazione console per creare un progetto di applicazione console che dispone già dei riferimenti al progetto e dei file essenziali.  
  
 In genere, un'applicazione console viene compilata in un file eseguibile autonomo ma non dispone di un'interfaccia grafica. Un utente esegue l'applicazione console da un prompt dei comandi e usa quest'ultimo per inviare le istruzioni all'applicazione in esecuzione. Anche al prompt dei comandi l'applicazione fornisce informazioni sull'output. L'immediatezza di un'applicazione console consente di imparare le tecniche di programmazione senza preoccuparsi di implementare un'interfaccia grafica.  
  
 Quando si usa il modello di applicazione console per creare un progetto, vengono aggiunti automaticamente i riferimenti e i file seguenti:  
  
-   Riferimenti a questi spazi dei nomi di .NET Framework:  
  
    -   [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx) \- Contiene le classi fondamentali e le classi base che definiscono i valori usati comunemente e i tipi di dati di riferimento, gli eventi e i gestori eventi, le interfacce, le eccezioni di elaborazione e gli attributi.  
  
    -   mscorlib \- DLL di assembly che supporta lo sviluppo in .NET Framework.  
  
-   File di origine:  
  
    -   Console \(file con estensione cpp\) \- File sorgente principale e punto di ingresso nell'applicazione appena creata. Identifica il file con estensione dll e lo spazio dei nomi del progetto. Fornire il proprio codice in questo file.  
  
    -   AssemblyInfo.cpp \- Contiene attributi, file, risorse, tipi, informazioni sulla versione e sulla firma e così via che è possibile usare per modificare i metadati dell'assembly del progetto. Per altre informazioni, vedere [Contenuto degli assembly](../Topic/Assembly%20Contents.md).  
  
    -   Stdafx.cpp \- Usato per compilare un file di intestazione precompilato denominato Win32.pch e un file di tipi precompilati denominato StdAfx.obj.  
  
-   File di intestazione:  
  
    -   Stdafx.h \- Usato per compilare un file di intestazione precompilato denominato Win32.pch e un file di tipi precompilati denominato StdAfx.obj.  
  
    -   resource.h \- File di inclusione generato per app.rc.  
  
-   File di risorse:  
  
    -   app.rc: \- File script di risorse di un programma.  
  
    -   app.ico \- File icona di un programma.  
  
-   ReadMe.txt \- Descrive i file nel progetto.  
  
## Per creare un'applicazione console Common Language Runtime \(CLR\)  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo Progetto** sotto **Modelli installati**, selezionare il nodo **Visual C\+\+**, quindi **CLR** e infine il modello Applicazione console.  
  
3.  Nella casella **Nome** immettere un nome univoco per l'applicazione.  
  
     È possibile specificare altre impostazioni di progetto e di soluzione, anche se non sono necessarie.  
  
4.  Fare clic sul pulsante **OK**.  
  
## Vedere anche  
 [NOTINBUILD Procedura: Creare applicazioni console CLR](http://msdn.microsoft.com/it-it/b8af4197-e65f-4b17-b18e-b9e92965d026)   
 [Progetti CLR](../ide/files-created-for-clr-projects.md)   
 [NIB: Gestione degli elementi nei progetti](http://msdn.microsoft.com/it-it/762e606b-7f44-4b66-97a1-e30a703654a0)