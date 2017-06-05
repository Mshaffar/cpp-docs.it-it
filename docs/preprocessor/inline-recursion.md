---
title: "inline_recursion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "inline_recursion_CPP"
  - "vc-pragma.inline_recursion"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inline_recursion (pragma)"
  - "pragma, inline_recursion"
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# inline_recursion
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Controlla l'espansione inline delle chiamate di funzione dirette o ricorsive reciproche.  
  
## Sintassi  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## Note  
 Utilizzare questo pragma per controllare le funzioni contrassegnate come [inline](../misc/inline-inline-forceinline.md) e [\_\_inline](../misc/inline-inline-forceinline.md) o le funzioni che il compilatore espande automaticamente con l'opzione \/Ob2.  L'utilizzo di questo pragma richiede l'impostazione dell'opzione del compilatore [\/Ob](../build/reference/ob-inline-function-expansion.md) 1 o 2.  Lo stato predefinito per `inline_recursion` è disattivata.  Questo pragma viene applicato alla prima chiamata di funzione dopo che il pragma viene rilevato e non influisce sulla definizione della funzione.  
  
 Il pragma `inline_recursion` controlla la modalità di espansione delle funzioni ricorsive.  Se `inline_recursion` è disattivato e se una funzione inline chiama se stessa \(direttamente o indirettamente\), la funzione viene espansa solo una volta.  Se `inline_recursion` è attivo, la funzione viene espansa più volte finché non raggiunge il valore impostato con il pragma [inline\_depth](../preprocessor/inline-depth.md), il valore predefinito per le funzioni ricorsive definito dal pragma `inline_depth` o un limite di capacità.  
  
## Vedere anche  
 [Direttive pragma e parola chiave \_\_Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline\_depth](../preprocessor/inline-depth.md)   
 [\/Ob \(Espansione funzioni inline\)](../build/reference/ob-inline-function-expansion.md)