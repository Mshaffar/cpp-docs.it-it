---
title: "UNIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unix"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compatibilità con POSIX"
  - "nomi di file POSIX"
  - "UNIX"
  - "UNIX, compatibilità"
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# UNIX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se si intende eseguire il porting dei programmi in UNIX, attenersi alle seguenti linee guida:  
  
-   Non rimuovere i file di intestazione dalla sottodirectory SYS.  È possibile inserire i file di intestazione di SYS altrove solo se non si intende portare i programmi su UNIX.  
  
-   Utilizzare il delimitatore di percorso compatibile con UNIX nelle routine che accettano stringhe che rappresentano i percorsi e i nomi di file come argomenti.  Per questo scopo UNIX supporta solo la barra \(\/\), mentre i sistemi operativi Win32 supportano sia la barra rovesciata \(\\\) che la barra \(\/\).  Questa documentazione utilizza quindi le barre compatibili con UNIX, ad esempio come delimitatori del percorso nelle istruzioni `#include`. \(Tuttavia, la shell dei comandi del sistema operativo Windows, CMD.EXE, non supporta la barra nei comandi immessi nel prompt dei comandi.\)  
  
-   Utilizzare i percorsi e i nomi di file che funzionano correttamente in UNIX, in cui viene applicata la distinzione tra maiuscole e minuscole.  Il file system tabella di allocazione file \(FAT\) nei sistemi operativi Win32 non applica la distinzione tra maiuscole e minuscole; il file system NTFS preserva le maiuscole e minuscole per gli elenchi delle directory, ma le ignora nelle ricerche dei file e in altre operazioni di sistema.  
  
    > [!NOTE]
    >  In questa versione di Visual C\+\+, le informazioni di compatibilità con UNIX sono state rimosse dalle descrizioni delle funzioni.  
  
## Vedere anche  
 [Compatibilità](../c-runtime-library/compatibility.md)