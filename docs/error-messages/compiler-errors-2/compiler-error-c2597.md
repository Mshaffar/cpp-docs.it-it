---
title: "Errore del compilatore C2597 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2597"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2597"
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Errore del compilatore C2597
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

riferimento non valido al membro non statico 'identifier'  
  
 Possibili cause:  
  
1.  Viene specificato un membro non statico in una funzione membro statica.  Per accedere al membro non statico, è necessario passare o creare un'istanza locale della classe e usare un operatore di accesso membri \(`.` o `->`\).  
  
2.  L'identificatore specificato non è un membro di una classe, struttura o unione.  Controllare l'ortografia dell'identificatore.  
  
3.  Un operatore di accesso al membro fa riferimento a una funzione non membro.  
  
4.  L'esempio seguente genera l'errore C2597 e mostra come risolverlo:  
  
```  
// C2597.cpp  
// compile with: /c  
struct s1 {  
   static void func();  
   static void func2(s1&);  
   int i;  
};  
  
void s1::func() {  
   i = 1;    // C2597 - static function can't access non-static data member  
}  
  
// OK - fix by passing an instance of s1  
void s1::func2(s1& a) {  
   a.i = 1;  
}  
  
```