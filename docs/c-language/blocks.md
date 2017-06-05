---
title: "Blocks | Microsoft Docs"
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
  - "blocchi"
  - "istruzione composta"
  - "definizioni di funzioni, blocchi nel codice"
  - "istruzioni, composito"
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Blocks
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una sequenza di dichiarazioni, definizioni e istruzioni racchiuse tra parentesi graffe \(**{ }**\) viene definita un "blocco". Esistono due tipi di blocchi nel linguaggio C.  L'"istruzione composta", un'istruzione composta da una o più istruzioni \(vedere\) [Istruzione composta](../c-language/compound-statement-c.md)\), è un tipo di blocco.  L'altro, "definizione di funzione", è costituito da un'istruzione composta \(il corpo della funzione\) e dall'"intestazione" associata della funzione \(il nome della funzione, il tipo restituito e i parametri formali\).  Un blocco all'interno di altri viene definito "annidato".  
  
 Si noti che mentre tutte le istruzioni composte sono racchiuse tra parentesi graffe, non tutti gli elementi racchiusi tra parentesi graffe sono un'istruzione composta.  Ad esempio, sebbene le specifiche di elementi matrice, struttura o di enumerazione possano trovarsi tra parentesi graffe, non sono istruzioni composte.  
  
## Vedere anche  
 [File e programmi di origine](../c-language/source-files-and-source-programs.md)