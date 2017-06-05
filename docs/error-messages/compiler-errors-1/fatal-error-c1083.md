---
title: Errore irreversibile C1083 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1083
dev_langs:
- C++
helpviewer_keywords:
- C1083
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
caps.latest.revision: 23
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: bbc5e1f78ca1ea15e65fdd76b7ecd2ea0e195b00
ms.contentlocale: it-it
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1083"></a>Errore irreversibile C1083
Impossibile aprire il file tipofile: 'file': messaggio  
  
 Il compilatore genera un errore C1083 quando non trova un file. Di seguito sono riportate le cause più comuni di questo errore.  
  
 **Il nome file specificato non è corretto**  
  
 Nome di un file digitato in modo non corretto. Di seguito è riportato un esempio:  
  
```cpp  
#include <algorithms.h>  
```  
  
 potrebbe non trovare il file richiesto. È un libreria Standard C++ file di intestazione denominato algorithms che non dispone di un'estensione di file con estensione h. Non viene trovato tramite questa direttiva `include`. Per risolvere il problema, verificare che sia stato immesso il nome del file corretto.  
  
 Alcune intestazioni della libreria di runtime C risiedono in una sottodirectory della directory include standard. Per includere sys\types.h, ad esempio, è necessario includere il nome della sottodirectory sys nella direttiva include:  
  
 `#include <sys\types.h>`  
  
 **Il file non è incluso nel percorso di ricerca del compilatore**  
  
 Il compilatore non trova il file utilizzando le regole di ricerca indicate da una direttiva `include` o `import`. ad esempio, un file di intestazione racchiuso tra virgolette  
  
 `#include "myincludefile.h"`  
  
 indica al compilatore di cercare il file nella stessa directory che contiene il file di origine e quindi di cercarlo in altri percorsi specificati dall'ambiente di compilazione. Se le virgolette contengono un percorso assoluto, il compilatore cerca il file solo in quel percorso. Se le virgolette contengono un percorso relativo, il compilatore cerca il file nella directory relativa alla directory di origine. Se il nome è racchiuso tra parentesi angolari  
  
 `#include <stdio.h>`  
  
 il compilatore segue un percorso di ricerca definito dall'ambiente di compilazione, il **/I** opzione del compilatore di **/X** opzione del compilatore e **INCLUDE** variabile di ambiente. Per ulteriori informazioni, inclusi i dettagli specifici sull'ordine di ricerca utilizzato per trovare un file, vedere [#include (direttiva) (C/C++)](../../preprocessor/hash-include-directive-c-cpp.md) e [#import direttiva](../../preprocessor/hash-import-directive-cpp.md).  
  
 Anche quando il file di intestazione sono elencati nel **Esplora** come parte di un progetto, i file vengono trovati solo dal compilatore quando vengono definite da un `include` o `import` direttiva e sono posizionati in un percorso di ricerca di directory. Tipi diversi di compilazioni possono usare percorsi di ricerca diversi. Il **/X** possibile utilizzare l'opzione del compilatore per escludere directory dal percorso di ricerca di file di inclusione. In questo modo, compilazioni diverse possono utilizzare file di inclusione diversi con lo stesso nome, ma archiviati in directory diverse. Si tratta di un'alternativa alla compilazione condizionale utilizzando i comandi del preprocessore. Per ulteriori informazioni sul **/X** l'opzione del compilatore, vedere [/X (Ignora a percorsi di inclusione Standard)](../../build/reference/x-ignore-standard-include-paths.md).  
  
 Quando il compilatore viene richiamato sulla riga di comando, vengono spesso usate variabili di ambiente per specificare i percorsi di ricerca. Se il percorso di ricerca descritto dal **INCLUDE** variabile di ambiente non è impostata correttamente, viene generato un errore C1083. Per ulteriori informazioni su come usare le variabili di ambiente, vedere [procedura: utilizzare variabili di ambiente in una Build](/visualstudio/msbuild/how-to-use-environment-variables-in-a-build).  
  
 Per risolvere il problema, correggere il percorso usato dal compilatore per trovare il file importato o incluso. Un nuovo progetto utilizza i percorsi di ricerca predefiniti. Potrebbe essere necessario modificare il percorso per aggiungere una directory per il progetto. Se esegue la compilazione sulla riga di comando, impostare il **INCLUDE** variabile di ambiente o **/I** l'opzione del compilatore per specificare il percorso del file. Per impostare il percorso di directory di inclusione in Visual Studio, aprire il progetto **pagine delle proprietà** finestra di dialogo espandere **le proprietà di configurazione** e **directory di VC + +**, quindi modificare il **directory di inclusione** valore. Per ulteriori informazioni sulle directory per ogni progetto e per utente eseguire la ricerca dal compilatore in Visual Studio, vedere [pagina delle proprietà directory di VC + +](../../ide/vcpp-directories-property-page.md). Per ulteriori informazioni sul **/I** l'opzione del compilatore, vedere [/I (directory di inclusione aggiuntive)](../../build/reference/i-additional-include-directories.md).  
  
 **La versione errata di un nome di file è inclusa**  
  
 L'errore C1083 può anche indicare che è stata inclusa la versione non corretta di un file. È ad esempio possibile che una compilazione includa la versione non corretta di un file contenente una direttiva `include` per un file di intestazione non destinato a questa compilazione. Se il file di intestazione non viene trovato, viene generato l'errore C1083. La soluzione al problema consiste nell'utilizzare il file corretto e non nell'aggiungere il file di intestazione o la directory alla compilazione.  
  
 **Le intestazioni precompilate non sono ancora precompilate**  
  
 Quando un progetto è configurato per l'utilizzo di intestazioni precompilate, è necessario creare i file pch corrispondenti in modo da poter compilare i file che utilizzano il contenuto dell'intestazione. Ad esempio, il file stdafx.cpp file viene creato automaticamente nella directory del progetto per nuovi progetti MFC. Compilare innanzitutto il file per creare i file di intestazione precompilati. (Nella progettazione del processo di compilazione questo avviene automaticamente.) Per ulteriori informazioni, vedere [la creazione di file di intestazione precompilata](../../build/reference/creating-precompiled-header-files.md).  
  
 **Cause aggiuntive**  
  
-   Il file utilizza il codice gestito, ma l'opzione del compilatore **/clr** non è specificato. Per altre informazioni, vedere [/clr (Compilazione Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
-   Il file viene compilato utilizzando un altro **/ANALYZE** impostazione dell'opzione del compilatore rispetto a quella utilizzata per precompilare le intestazioni. (Quando le intestazioni per un progetto vengono precompilate, tutte utilizzano lo stesso **/ANALYZE** impostazioni.) Per altre informazioni, vedere [/analyze (Analisi codice)](../../build/reference/analyze-code-analysis.md).  
  
-   Il file, la directory o il disco è di sola lettura.  
  
-   Le autorizzazioni di accesso per il file o la directory non vengono concesse.  
  
-   Gli handle di file non sono sufficienti. Chiudere alcune applicazioni e compilare nuovamente. Questa condizione è insolita in circostanze tipiche. Può tuttavia verificarsi quando vengono compilati progetti di grandi dimensioni in un computer con memoria fisica limitata.  
  
 Nell'esempio seguente viene generato l'errore C1083.  
  
```  
// C1083.cpp  
// compile with: /c  
#include "test.h"   // C1083 test.h does not exist  
#include "stdio.h"   // OK  
```  
  
 Per informazioni su come compilare progetti C/C++ nell'IDE o sulla riga di comando e informazioni sull'impostazione delle variabili di ambiente, vedere [compilazione di programmi C/C++](../../build/building-c-cpp-programs.md).
 
 ## <a name="see-also"></a>Vedere anche
 [Proprietà di MSBuild](/visualstudio/msbuild/msbuild-properties)