---
title: "Errore irreversibile C1017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1017"
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Errore irreversibile C1017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

espressione costante integer non valida  
  
 L'espressione all'interno di una direttiva `#if` non esiste o non dà come risultato una costante.  
  
 È necessario che le costanti definite con `#define` includano valori che restituiscono una costante intera se utilizzati in una direttiva `#if`, `#elif` o `#else`.  
  
 Il seguente codice di esempio genera l'errore C1017:  
  
```  
// C1017.cpp  
#define CONSTANT_NAME "YES"  
#if CONSTANT_NAME   // C1017  
#endif  
```  
  
 Possibile soluzione:  
  
```  
// C1017b.cpp  
// compile with: /c  
#define CONSTANT_NAME 1  
#if CONSTANT_NAME  
#endif  
```  
  
 Poiché `CONSTANT_NAME` dà come risultato un valore stringa e non integer, la direttiva `#if` genera l'errore irreversibile C1017.  
  
 In altri casi, una costante non definita viene valutata come zero dal preprocessore.  Tale situazione può comportare risultati indesiderati, come illustrato nell'esempio seguente.  `YES` non è definito, pertanto restituisce zero.  L'espressione `#if` `CONSTANT_NAME` restituisce false e il codice da utilizzare in `YES` viene rimosso dal preprocessore.  Neanche `NO` è definito \(zero\), pertanto l'espressione `#elif` `CONSTANT_NAME==NO` restituisce true \(`0 == 0`\) e il preprocessore lascia il codice nella parte `#elif` dell'istruzione, eseguendo esattamente l'opposto del comportamento previsto.  
  
```  
// C1017c.cpp  
// compile with: /c  
#define CONSTANT_NAME YES  
#if CONSTANT_NAME  
   // Code to use on YES...  
#elif CONSTANT_NAME==NO  
   // Code to use on NO...  
#endif  
```  
  
 Per sapere con esattezza come vengono gestite le direttive per il preprocessore in fase di compilazione, utilizzare [\/P](../../build/reference/p-preprocess-to-a-file.md), [\/E](../../build/reference/e-preprocess-to-stdout.md) o [\/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).