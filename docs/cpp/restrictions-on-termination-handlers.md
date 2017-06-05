---
title: "Limitazioni ai gestori di terminazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "restrizioni, gestori di terminazione"
  - "gestori di terminazione, limiti"
  - "try-catch (parola chiave) [C++], gestori di terminazione"
ms.assetid: 8b1cb481-303f-4e79-b409-57a002a9fa9e
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Limitazioni ai gestori di terminazione
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Non è possibile utilizzare un'istruzione `goto` per eseguire un salto in un blocco di istruzioni `__try` o `__finally`.  È tuttavia necessario inserire il blocco di istruzioni attraverso il normale flusso di controllo. È tuttavia possibile eseguire un salto da un blocco di istruzioni `__try`. Non è inoltre possibile annidare un gestore eccezioni o un gestore di terminazione all'interno di un blocco `__finally`.  
  
 Inoltre, alcuni tipi di codice consentiti in un gestore di terminazione producono risultati inaffidabili, pertanto è necessario utilizzarli con cautela.  Uno è un'istruzione `goto` che esegue il salto da un blocco di istruzioni `__finally`.  Se il blocco viene eseguito come parte della terminazione normale, non si verifica nulla di anomalo.  Tuttavia, se il sistema sta eseguendo la rimozione dello stack, tale rimozione viene arrestata e la funzione corrente acquisisce il controllo come se non si fosse verificata alcuna terminazione anomala.  
  
 Un'istruzione `return` all'interno di un blocco di istruzioni `__finally` presenta all'incirca la stessa situazione.  Il controllo torna al chiamante della funzione contenente il gestore di terminazione.  Nel caso in cui il sistema stesse eseguendo la rimozione dello stack, tale processo viene interrotto e il programma procede come se non fosse stata generata alcuna eccezione.  
  
## Vedere anche  
 [Scrittura di un gestore di terminazione](../cpp/writing-a-termination-handler.md)   
 [Gestione strutturata delle eccezioni](../cpp/structured-exception-handling-c-cpp.md)