---
title: "Conversioni aritmetiche comuni | Microsoft Docs"
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
  - "conversioni aritmetiche [C++]"
  - "operatori aritmetici [C++], tipo (conversione)"
  - "conversioni [C++], aritmetici"
  - "conversione di tipi di dati [C++], aritmetici"
  - "operatori [C], conversioni aritmetiche"
  - "conversione di tipi [C++], aritmetici"
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Conversioni aritmetiche comuni
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La maggior parte degli operatori C eseguono conversioni di tipi per impostare gli operandi di un'espressione a un tipo comune o per estendere valori short nella dimensione dell'Integer utilizzata nelle operazioni del computer.  Le conversioni eseguite dagli operatori C dipendono dall'operatore specifico e dal tipo di operando o di operandi.  Tuttavia, molti operatori eseguono conversioni simili su operandi di tipi integrali e a virgola mobile.  Queste conversioni sono note come "conversioni aritmetiche". La conversione di un valore operando in un tipo compatibile non comporta alcuna modifica al valore.  
  
 Le conversioni aritmetiche riepilogate di seguito vengono definite "conversioni aritmetiche comuni". Questi passaggi si applicano solo agli operatori binari che prevedono il tipo aritmetico.  Lo scopo è quello di produrre un tipo comune che è anche il tipo del risultato.  Per determinare quali conversioni vengono effettivamente eseguite, il compilatore applica l'algoritmo seguente alle operazioni binarie nell'espressione.  I passaggi riportati di seguito non sono in un ordine di precedenza.  
  
1.  Se uno degli operandi è di tipo `long double`, l'altro operando verrà convertito nel tipo `long double`.  
  
2.  Se la condizione precedente non viene soddisfatta e uno degli operandi è di tipo **double**, l'altro operando verrà convertito nel tipo **double**.  
  
3.  Se le due condizioni precedenti non vengono soddisfatte e uno degli operandi è di tipo **float**, l'altro operando verrà convertito nel tipo **float**.  
  
4.  Se le tre condizioni precedenti non vengono soddisfatte \(nessuno degli operandi è di tipo a virgola mobile\), le conversioni integrali verranno eseguite sugli operandi come segue:  
  
    -   Se uno degli operandi è di tipo `unsigned long`, l'altro operando verrà convertito nel tipo `unsigned long`.  
  
    -   Se la condizione precedente non viene soddisfatta e uno degli operandi è di tipo **long** e l'altro operando di tipo `unsigned int`, entrambi gli operandi verranno convertiti nel tipo `unsigned long`.  
  
    -   Se le due condizioni precedenti non vengono soddisfatte e uno degli operandi è di tipo **long**, l'altro operando verrà convertito nel tipo **long**.  
  
    -   Se le tre condizioni precedenti non vengono soddisfatte e uno degli operandi è di tipo `unsigned int`, l'altro operando verrà convertito nel tipo `unsigned int`.  
  
    -   Se nessuna delle condizioni precedenti viene soddisfatta, entrambi verranno convertiti nel tipo `int`.  
  
 Nell'esempio di codice seguente vengono illustrate queste regole di conversione:  
  
```  
float   fVal;  
double  dVal;  
int   iVal;  
unsigned long ulVal;  
  
dVal = iVal * ulVal; /* iVal converted to unsigned long  
                      * Uses step 4.  
                      * Result of multiplication converted to double   
                      */  
dVal = ulVal + fVal; /* ulVal converted to float  
                      * Uses step 3.  
                      * Result of addition converted to double   
                      */   
```  
  
## Vedere anche  
 [Operatori C](../c-language/c-operators.md)