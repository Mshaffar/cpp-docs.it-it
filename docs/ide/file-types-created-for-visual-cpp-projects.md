---
title: "Tipi di file creati per i progetti di Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "file di intestazione [C++], progetti Visual C++"
  - "ActiveX (controlli) [C++], file della Guida"
  - "def (file)"
  - "elementi del progetto [C++], file"
  - "progetti Visual C++, file e directory"
  - "file di risorse, creati dalla procedura guidata"
  - "file [C++], estensioni"
  - "file della Guida, per controlli ActiveX"
  - "progetti Web [C++], aggiunta di elementi"
  - ".def (file)"
  - "concessione in licenza di controlli ActiveX"
ms.assetid: 2b0ee2e0-ae81-4185-9bb9-11da3c99a283
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipi di file creati per i progetti di Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Questo argomento descrive tutti i tipi di file associati ai progetti di Visual C\+\+ per le applicazioni desktop classiche. I file effettivamente inclusi nel progetto dipendono dal tipo di progetto e dalle opzioni selezionate nella procedura guidata.  
  
-   [File di soluzioni e di progetto](../ide/project-and-solution-files.md)  
  
-   [Progetti CLR](../ide/files-created-for-clr-projects.md)  
  
-   [File di intestazione e di origine di un controllo o programma ATL](../ide/atl-program-or-control-source-and-header-files.md)  
  
-   [File di intestazione e di origine di un controllo o di un programma MFC](../ide/mfc-program-or-control-source-and-header-files.md)  
  
-   [File di intestazione precompilata](../ide/precompiled-header-files.md)  
  
-   [File di risorse](../ide/resource-files-cpp.md)  
  
-   [File della Guida \(WinHelp\)](../ide/help-files-winhelp.md)  
  
-   [File dei suggerimenti](../ide/hint-files.md)  
  
 L'operazione di [creazione di un progetto di Visual C\+\+](../ide/creating-desktop-projects-by-using-application-wizards.md) può consistere nella creazione di una nuova soluzione oppure nell'aggiunta di un progetto a una soluzione. Le applicazioni complesse vengono in genere sviluppate includendo più progetti in una soluzione.  
  
 I progetti di solito producono un file EXE o una DLL e possono dipendere l'uno dall'altro. Durante il processo di compilazione, l'ambiente di Visual C\+\+ verifica le dipendenze sia all'interno di un progetto che tra i diversi progetti. Ogni progetto dispone di un codice sorgente di base e, a seconda del tipo, può comprendere numerosi altri file che ne contengono i vari aspetti. Il contenuto di questi file è indicato dalla relativa estensione. L'ambiente di sviluppo di Visual Studio usa le estensioni di file per determinare come gestire il contenuto dei file durante la compilazione.  
  
 La tabella riportata di seguito illustra i file comuni dei progetti di Visual C\+\+, identificandone l'estensione corrispondente.  
  
|Estensione di file|Tipo|Contenuto|  
|------------------------|----------|---------------|  
|asmx|Origine|File di distribuzione.|  
|asp|Origine|File Active Server Page.|  
|atp|Progetto|File di progetto del modello di applicazione.|  
|bmp, dib, gif, jpg, jpe, png|Risorsa|File di immagine generali.|  
|bsc|Compilazione|File di codice del browser.|  
|cpp; c|Origine|File di codice sorgente principali per l'applicazione.|  
|cur|Risorsa|File grafico bitmap di cursore.|  
|dbp|Progetto|File di progetto di database.|  
|disco|Origine|File di documento di individuazione dinamica. Gestisce l'individuazione di servizi Web XML.|  
|exe, dll|Progetto|File eseguibili o di libreria a collegamento dinamico.|  
|h|Origine|File di intestazione o di inclusione.|  
|htm, html, xsp, asp, htc, hta, xml|Risorsa|File Web comuni.|  
|HxC|Progetto|File di progetto della Guida.|  
|ico|Risorsa|File grafico bitmap di icona.|  
|idb|Compilazione|File di stato, contenente le informazioni sulle dipendenze tra i file di origine e le definizioni delle classi, che può essere usato dal compilatore durante la ricompilazione minima e la compilazione incrementale. Per specificare il nome del file con estensione idb, usare l'opzione [\/Fd](../build/reference/fd-program-database-file-name.md) del compilatore. Per altre informazioni, vedere [\/Gm \(Abilita ricompilazione minima\)](../build/reference/gm-enable-minimal-rebuild.md).|  
|idl|Compilazione|File del linguaggio di definizione dell'interfaccia. Per altre informazioni, vedere [File di definizione dell'interfaccia \(IDL\)](http://msdn.microsoft.com/library/windows/desktop/aa378712) in [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].|  
|ilk|Collegamento|File di collegamento incrementale. Per altre informazioni, vedere [\/INCREMENTAL](../build/reference/incremental-link-incrementally.md).|  
|map|Collegamento|File di testo contenente informazioni sul linker. Per denominare il file con estensione map, usare l'opzione [\/Fm](../build/reference/fm-name-mapfile.md) del compilatore. Per altre informazioni, vedere [\/MAP](../build/reference/map-generate-mapfile.md).|  
|mfcribbon\-ms|Risorsa|File di risorse contenente il codice XML che definisce i pulsanti, i controlli e gli attributi della barra multifunzione. Per altre informazioni, vedere [Finestra di progettazione della barra multifunzione \(MFC\)](../mfc/ribbon-designer-mfc.md).|  
|obj, o||File oggetto, compilati ma non collegati.|  
|pch|Debug|File di intestazione precompilato.|  
|rc, rc2|Risorsa|[File script di risorsa](../mfc/working-with-resource-files.md) per generare risorse.|  
|sbr|Compilazione|File di origine intermedio del browser. File di input per [BSCMAKE](../build/reference/bscmake-options.md).|  
|sln|Soluzione|File di [soluzione](http://msdn.microsoft.com/it-it/a45c299d-69f5-4b67-879d-1383417df0a7).|  
|suo|Soluzione|File di opzioni di soluzione.|  
|txt|Risorsa|File di testo, in genere il file Readme.|  
|vap|Progetto|File di progetto di Visual Studio Analyzer.|  
|vbg|Soluzione|File del gruppo di progetti compatibili.|  
|vbp, vip, vbproj|Progetto|File di progetto Visual Basic.|  
|vcxproj|Progetto|File di progetto Visual C\+\+. Per altre informazioni, vedere [Makefile e file di progetto](../ide/project-and-solution-files.md).|  
|vcxproj.filters|Progetto|Quando si usa Esplora soluzioni per aggiungere un file a un progetto, il file dei filtri definisce la posizione nella visualizzazione albero di Esplora soluzioni in cui viene aggiunto il file, in base alla relativa estensione.|  
|vdproj|Progetto|File di progetto di distribuzione Visual Studio.|  
|vmx|Progetto|File di progetto macro.|  
|vup|Progetto|File di progetto di utilità.|  
  
 Per informazioni sugli altri file associati a Visual Studio, vedere [Tipi di file ed estensioni in Visual Studio .NET](../Topic/Project%20and%20Solution%20File%20Types.md).  
  
 I file di progetto vengono organizzati in cartelle in Esplora soluzioni. Visual C\+\+ crea cartelle per i file di origine, di intestazione e di risorse, ma è possibile riorganizzare queste cartelle o crearne di nuove. Le cartelle consentono di organizzare esplicitamente cluster logici di file all'interno della gerarchia di un progetto. Ad esempio, è possibile creare cartelle per tutti i file di origine dell'interfaccia utente oppure per gruppi di programmi di prova, specifiche o test. Tutti i nomi delle cartelle di file devono essere univoci.  
  
 Quando si aggiunge un elemento a un progetto, l'elemento viene aggiunto a tutte le configurazioni del progetto, indipendentemente dal fatto che l'elemento possa essere compilato. Se ad esempio si dispone di un progetto denominato Progetto, l'elemento viene aggiunto sia alla configurazione di debug del progetto che a quella di rilascio.  
  
## Vedere anche  
 [Creazione e gestione di progetti Visual C\+\+](../ide/creating-and-managing-visual-cpp-projects.md)   
 [Tipi di progetto Visual C\+\+](../ide/visual-cpp-project-types.md)   
 [Supporto della procedura guidata per altre lingue](../ide/wizard-support-for-other-languages.md)