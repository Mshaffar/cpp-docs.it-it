---
title: "Errore del compilatore C2064 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2064"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2064"
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Errore del compilatore C2064
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

il termine non restituisce una funzione che accetta N argomenti  
  
 Viene effettuata una chiamata a una funzione tramite un'espressione.  L'espressione non restituisce un puntatore a una funzione che accetta il numero specificato di argomenti.  
  
 In questo esempio, il codice tenta di chiamare non funzioni come funzioni.  L'esempio seguente generato l'errore C2064:  
  
```  
// C2064.cpp  
int i, j;  
char* p;  
void func() {  
   j = i();    // C2064, i is not a function  
   p();        // C2064, p doesn't point to a function  
}  
```  
  
 È necessario chiamare i puntatori a funzioni membro non statiche dal contesto dell'istanza di un oggetto.  L'esempio seguente genera l'errore C2064 e mostra come risolverlo:  
  
```  
// C2064b.cpp  
struct C {  
   void func1(){}  
   void func2(){}  
};  
  
typedef void (C::*pFunc)();  
  
int main() {  
   C c;  
   pFunc funcArray[2] = {&C::func1, &C::func2};  
   (funcArray[0])();    // C2064   
   (c.*funcArray[0])(); // OK - function called in instance context  
}  
  
```  
  
 All'interno di una classe, i puntatori a funzioni membro devono indicare anche il contesto dell'oggetto chiamante.  L'esempio seguente genera l'errore C2064 e mostra come risolverlo:  
  
```  
// C2064d.cpp  
// Compile by using: cl /c /W4 C2064d.cpp  
struct C {  
   typedef void (C::*pFunc)();  
   pFunc funcArray[2];  
   void func1(){}  
   void func2(){}  
   C() {  
      funcArray[0] = &C::func1;  
      funcArray[1] = &C::func2;  
   }  
   void func3() {  
      (funcArray[0])();   // C2064  
      (this->*funcArray[0])(); // OK - called in this instance context  
   }  
};  
```