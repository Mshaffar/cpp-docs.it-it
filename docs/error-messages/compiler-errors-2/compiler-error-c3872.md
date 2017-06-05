---
title: "Errore del compilatore C3872 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3872"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3872"
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Errore del compilatore C3872
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'char': carattere non consentito in un identificatore  
  
 Il compilatore C\+\+ è conforme allo standard C\+\+11 sui caratteri consentiti in un identificatore. In un identificatore sono consentiti solo alcuni intervalli di caratteri e di nomi di caratteri universali. Sono previste ulteriori restrizioni per il carattere iniziale di un identificatore. Per altre informazioni e per un elenco degli intervalli di caratteri e di nomi di caratteri universali consentiti, vedere [Identificatori C\+\+](../../cpp/identifiers-cpp.md).  
  
 L'intervallo di caratteri consentiti in un identificatore è meno restrittivo quando si compila codice C\+\+\/CLI. Gli identificatori nel codice compilato con \/clr devono essere conformi allo [standard ECMA\-335: Common Language Infrastructure \(CLI\)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 L'esempio seguente genera l'errore C3872:  
  
```  
// C3872.cpp int main() { int abc_\u0040;   // C3872, U+0040 is in base char set int abc_\u3001;   // C3872, U+3001 is not in allowed range int \u30A2_abc_\u3042;   // OK, UCNs in allowed range }  
```