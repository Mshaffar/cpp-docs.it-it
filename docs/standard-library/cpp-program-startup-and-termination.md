---
title: Avvio e chiusura di un programma C++ | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
caps.latest.revision: 9
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 53e31f3f3a175013a248401f4231bb87cf444681
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="c-program-startup-and-termination"></a>Avvio e chiusura di un programma C++
Un programma C++ esegue le stesse operazioni eseguite da un programma C all'avvio e alla chiusura del programma, nonché alcune altre descritte in questo argomento.  
  
 Prima che l'ambiente di destinazione chiami la funzione `main` e dopo aver archiviato i valori costanti iniziali specificati in tutti gli oggetti con una durata statica, il programma esegue i costruttori rimanenti per tali oggetti statici. L'ordine di esecuzione non viene specificato tra unità di conversione, ma si può comunque ritenere che alcuni oggetti [iostreams](../standard-library/iostreams-conventions.md) vengano inizializzati correttamente per l'uso da parte di questi costruttori statici. Questi flussi di testo di controllo sono:  
  
-   [cin](../standard-library/iostream.md#cin) - per l'input standard.  
  
-   [cout](../standard-library/iostream.md#cout) - per l'output standard.  
  
-   [cerr](../standard-library/iostream.md#cerr) - per l'output di errore standard non memorizzato nel buffer.  
  
-   [clog](../standard-library/iostream.md#clog) - per l'output di errore standard memorizzato nel buffer.  
  
 È anche possibile usare questi oggetti all'interno dei distruttori chiamati per gli oggetti statici durante la chiusura del programma.  
  
 Come con C, la restituzione da `main` o la chiamata di `exit` chiama tutte le funzioni registrate con `atexit` in ordine inverso del Registro di sistema. Un'eccezione generata da tale funzione registrata chiama `terminate`.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica sulla libreria standard C++](../standard-library/cpp-standard-library-overview.md)   
 [Thread safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)


