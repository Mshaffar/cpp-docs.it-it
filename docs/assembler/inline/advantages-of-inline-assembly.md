---
title: "Vantaggi dell&#39;assembly inline | Microsoft Docs"
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
  - "assembler [C++], vantaggi"
  - "assembly inline [C++], informazioni su assembly inline"
  - "assembly inline [C++], utilizzo"
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Vantaggi dell&#39;assembly inline
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Sezione specifica Microsoft  
 Poiché l'assembler inline non richiede un assembly separato e operazioni di collegamento, è più conveniente di un assembly separato.  Il codice assembly inline può utilizzare qualsiasi variabile C o nome di funzione inclusa nell'ambito, quindi può essere facilmente integrato con il codice C del programma.  Dato che il codice assembly può essere combinato inline con istruzioni C\+\+ o C, lo stesso può effettuare attività complesse o impossibili in C o C\+\+.  
  
 Gli utilizzi di assembly inline includono:  
  
-   Scrittura di funzioni in linguaggio assembly.  
  
-   Ottimizzazione spot delle sezioni di codice con velocità critica.  
  
-   Creazione di accesso diretto all'hardware per i driver di dispositivo.  
  
-   Scrittura di codice di prologo ed epilogo per chiamate "naked".  
  
 L'assembly inline è uno strumento per scopi specifici.  Se si desidera trasferire un'applicazione in computer diversi, è opportuno inserire il codice specifico per il computer in un modulo separato.  Poiché l'assembler inline non supporta tutte le direttive dati e macro Microsoft Macro Assembler \(MASM\), può essere utile utilizzare MASM per tali moduli.  
  
 **Fine sezione specifica Microsoft**  
  
## Vedere anche  
 [Assembler inline](../../assembler/inline/inline-assembler.md)