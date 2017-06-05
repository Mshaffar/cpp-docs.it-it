---
title: "Direttive per il preprocessore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "direttive, preprocessore"
  - "preprocessore, direttive"
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Direttive per il preprocessore
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Le direttive del preprocessore, quali `#define` e **\#ifdef**, vengono in genere utilizzate per semplificare la modifica dei programmi di origine ed eseguire più facilmente la compilazione in ambienti di esecuzione differenti.  Le direttive nel file di origine indicano al preprocessore di eseguire azioni specifiche.  Ad esempio, il preprocessore può sostituire i token nel testo, inserire il contenuto di altri file nel file di origine o eliminare la compilazione di parte del file rimuovendo sezioni di testo.  Le righe del preprocessore vengono riconosciute ed eseguite prima dell'espansione di una macro.  Pertanto, se una macro si espande in modo da risultare simile a un comando del preprocessore, tale comando non sarà riconosciuto dal preprocessore.  
  
 Le istruzioni del preprocessore utilizzano lo stesso set di caratteri delle istruzioni del file di origine, con l'eccezione che le sequenze di escape non sono supportate.  Il set di caratteri utilizzati nelle istruzioni del preprocessore equivale al [set di caratteri di esecuzione](http://msdn.microsoft.com/it-it/a7901c61-524d-47c6-beb6-d9dacc2e72ed).  Il preprocessore riconosce anche i valori di carattere negativi.  
  
 Il preprocessore riconosce le direttive seguenti:  
  
|||||  
|-|-|-|-|  
|[\#define](../preprocessor/hash-define-directive-c-cpp.md)|[\#error](../preprocessor/hash-error-directive-c-cpp.md)|[\#import](../preprocessor/hash-import-directive-cpp.md)|[\#undef](../preprocessor/hash-undef-directive-c-cpp.md)|  
|[\#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#include](../preprocessor/hash-include-directive-c-cpp.md)|[\#using](../preprocessor/hash-using-directive-cpp.md)|  
|[\#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#line](../preprocessor/hash-line-directive-c-cpp.md)|[\#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|  
|[\#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||  
  
 Il simbolo di cancelletto \(**\#**\) deve essere il primo carattere non spazio vuoto sulla riga contenente la direttiva; gli spazi vuoti possono apparire tra il simbolo di cancelletto e la prima lettera della direttiva.  Alcune direttive includono argomenti o valori.  Qualsiasi testo che segue una direttiva \(eccetto un argomento o un valore che fa parte di essa\) deve essere preceduto dal delimitatore di commento a riga singola \(**\/\/**\) o essere incluso tra delimitatori di commento \(**\/\* \*\/**\).  Le righe che contengono le direttive per il preprocessore possono essere continuate precedendo immediatamente il marcatore di fine riga con una barra rovesciata \(**\\**\).  
  
 Le direttive del preprocessore possono essere visualizzate in qualsiasi punto di un file di origine, ma si applicano solo al resto del file di origine.  
  
## Vedere anche  
 [Operatori del preprocessore](../preprocessor/preprocessor-operators.md)   
 [Macro predefinite](../preprocessor/predefined-macros.md)   
 [Riferimenti al preprocessore C\/C\+\+](../preprocessor/c-cpp-preprocessor-reference.md)