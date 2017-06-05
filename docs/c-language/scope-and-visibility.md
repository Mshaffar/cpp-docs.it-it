---
title: "Ambito e visibilit&#224; | Microsoft Docs"
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
  - "ambito file [C++]"
  - "ambito, livelli"
  - "visibilità"
ms.assetid: a019eb7c-66ed-46a7-bc9f-89a963930a56
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Ambito e visibilit&#224;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La "visibilità di un identificatore determina il suo "ambito", ovvero le parti del programma in cui è possibile fare riferimento allo stesso identificatore. Un identificatore è visibile \(ovvero, può essere utilizzato\) solo nelle parti di programma incluse nel suo "ambito" e che, al fine di incrementare la restrittività, possono essere limitate al file, alla funzione, al blocco o al prototipo di funzione in cui viene visualizzato l'identificatore stesso.  L'ambito di un identificatore corrisponde alla parte di programma in cui è possibile utilizzare il nome.  Questa parte del programma viene anche chiamata "ambito lessicale." Le tipologie di ambito sono quattro: funzione, file, blocco e prototipo di funzione.  
  
 L'ambito di tutti gli identificatori, ad eccezione delle etichette, viene determinato dal livello in cui si verifica la dichiarazione.  La visibilità degli identificatori all'interno dei programmi viene determinata dalle seguenti regole, specifiche per ogni tipologia:  
  
 Ambito di tipo file  
 Il dichiaratore, o identificatore di tipo, di un identificatore con ambito file appare all'esterno di qualunque blocco o elenco di parametri ed è accessibile da qualsiasi posizione nell'unità di conversione successivamente alla relativa dichiarazione.  I nomi degli identificatori con ambito file vengono spesso definiti "globali" o "esterni". L'ambito di un identificatore globale inizia in corrispondenza del punto della relativa definizione o dichiarazione e termina alla fine dell'unità di conversione.  
  
 Ambito di tipo funzione  
 L'etichetta è l'unico tipo di identificatore dotato di un ambito di tipo funzione.  L'etichetta viene dichiarata implicitamente quando viene utilizzata in un'istruzione.  I nomi delle etichette devono essere univoci all'interno di una funzione. \(Per ulteriori informazioni sulle etichette e sui nomi delle etichette, vedere [Le istruzioni goto e con etichetta](../c-language/goto-and-labeled-statements-c.md)\).  
  
 Ambito blocco  
 Il dichiaratore, o identificatore di tipo, di un identificatore con ambito blocco viene visualizzato all'interno di un blocco o nell'elenco delle dichiarazioni di parametro formale in una definizione di funzione.  È visibile solo dal punto della relativa dichiarazione o definizione alla fine del blocco che contiene la stessa dichiarazione o definizione.  Il suo ambito è limitato a tale blocco e a tutti i blocchi annidati nello stesso e termina alla parentesi graffa di chiusura del blocco associato.  Questo tipo di identificatori sono talvolta denominati "variabili locali."  
  
 Ambito di tipo prototipo di funzione  
 Il dichiaratore, o identificatore di tipo, di un identificatore con ambito di tipo prototipo di funzione viene visualizzato nell'elenco delle dichiarazioni di parametro presente in un prototipo di funzione, che non fa parte della dichiarazione di funzione.  Il suo ambito termina alla fine del dichiaratore di funzione.  
  
 Le dichiarazioni appropriate a rendere le variabili visibili in altri file di origine sono descritte in [Classi di archiviazione](../c-language/c-storage-classes.md).  Tuttavia, le variabili e le funzioni dichiarate a livello esterno attraverso l'identificatore di classe di archiviazione **statico** sono visibili solo all'interno del file di origine in cui sono definite.  Tutte le altre funzioni sono visibili a livello globale.  
  
## Vedere anche  
 [Durata, ambito, visibilità e collegamento](../c-language/lifetime-scope-visibility-and-linkage.md)