---
title: "comment (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.comment"
  - "comment_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "annotazioni [C++]"
  - "comment (pragma)"
  - "TODO (commenti) [C++], file compilati"
  - "pragma, commento"
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# comment (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inserisce un record di commento in un file oggetto o in un file eseguibile.  
  
## Sintassi  
  
```  
  
#pragma comment( comment-type [,"commentstring"] )  
```  
  
## Note  
 *comment\-type* è uno degli identificatori predefiniti, descritti di seguito, che specifica il tipo di record di commento.  L'elemento `commentstring` facoltativo è un valore letterale stringa che fornisce informazioni aggiuntive per alcuni tipi di commento.  Poiché `commentstring` è un valore letterale stringa, rispetta tutte le regole per tali valori per i caratteri di escape, le virgolette incorporate \(**"**\) e la concatenazione.  
  
 **compiler**  
 Inserisce il nome e il numero di versione del compilatore nel file oggetto.  Questo record di commento viene ignorato dal linker.  Se si fornisce un parametro `commentstring` per questo tipo di record, il compilatore genera un avviso.  
  
 **exestr**  
 Inserisce `commentstring` nel file oggetto.  In fase di collegamento questa stringa viene inserita nel file eseguibile.  La stringa non viene caricata in memoria quando viene caricato il file eseguibile, ma è disponibile con un programma che cerca le stringhe stampabili nei file.  Un utilizzo di questo tipo di record di commento prevede l'inclusione di un numero di versione o di informazioni simili in un file eseguibile.  
  
 `exestr` è deprecato e verrà rimosso nelle versioni future. Il linker non elabora il record di commento.  
  
 **lib**  
 Inserisce un record di ricerca nella libreria nel file oggetto.  Questo tipo di commento deve essere seguito da un parametro `commentstring` contenente il nome \(ed eventualmente il percorso\) della libreria in cui il linker esegue la ricerca.  Il nome della libreria segue i record di ricerca nella libreria predefiniti nel file oggetto. Il linker esegue la ricerca di tale libreria come se fosse stata denominata nella riga di comando, a condizione che la libreria non venga specificata con [\/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md).  È possibile inserire più record di ricerca nella libreria nello stesso file di origine. Ogni record viene visualizzato nel file oggetto nello stesso ordine in cui è stato individuato nel file di origine.  
  
 Se l'ordine della libreria predefinita e di una libreria aggiunta è importante, la compilazione con l'opzione [\/Zl](../build/reference/zl-omit-default-library-name.md) impedirà che il nome della libreria predefinita venga inserito nel modulo di oggetto.  Un secondo pragma di commento può quindi essere utilizzato per inserire il nome della libreria predefinita dopo la libreria aggiunta.  Le librerie elencate con tali pragma verranno visualizzate nel modulo di oggetto nello stesso ordine in cui vengono trovate nel codice sorgente.  
  
 **linker**  
 Inserisce un'[opzione del linker](../build/reference/linker-options.md) nel file oggetto.  È possibile utilizzare questo tipo di commento per specificare un'opzione del linker anziché passarla alla riga di comando o specificarla nell'ambiente di sviluppo.  È possibile ad esempio specificare l'opzione \/include per imporre l'inclusione di un simbolo:  
  
```  
#pragma comment(linker, "/include:__mySymbol")  
```  
  
 Solo le seguenti opzioni del linker \(*comment\-type*\) sono disponibili per essere passate all'identificatore del linker:  
  
-   [\/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)  
  
-   [\/EXPORT](../build/reference/export-exports-a-function.md)  
  
-   [\/INCLUDE](../build/reference/include-force-symbol-references.md)  
  
-   [\/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)  
  
-   [\/MERGE](../build/reference/merge-combine-sections.md)  
  
-   [\/SECTION](../build/reference/section-specify-section-attributes.md)  
  
 **utente**  
 Inserisce un commento generale nel file oggetto.  Il parametro `commentstring` contiene il testo del commento.  Questo record di commento viene ignorato dal linker.  
  
 Il pragma seguente indica al linker di eseguire la ricerca della libreria EMAPI.LIB durante il collegamento.  Il linker esegue la ricerca prima nella directory di lavoro, quindi nel percorso specificato nella variabile di ambiente LIB.  
  
```  
#pragma comment( lib, "emapi" )  
```  
  
 Il pragma seguente indica al compilatore di inserire il nome e il numero di versione del compilatore nel file oggetto:  
  
```  
#pragma comment( compiler )  
```  
  
> [!NOTE]
>  Per i commenti che accettano un parametro `commentstring`, è possibile utilizzare una macro in qualsiasi punto in cui si utilizzerebbe un valore letterale stringa purché la macro si espanda a un valore letterale stringa.  È inoltre possibile concatenare qualsiasi combinazione di valori letterali stringa e di macro che si espandono a valori letterali stringa.  L'istruzione seguente è ad esempio accettabile:  
  
```  
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )   
```  
  
## Vedere anche  
 [Direttive pragma e parola chiave \_\_Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)