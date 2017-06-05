---
title: "Avviso del compilatore (livello 4) C4460 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4460"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4460"
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Avviso del compilatore (livello 4) C4460
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

l'operatore WinRT o CLR 'operator' contiene un parametro passato per riferimento.La semantica dell'operatore WinRT o CLR 'operator' è diversa da quella dell'operatore C\+\+ 'operator'. Si intendeva passare il parametro per valore?  
  
 Si è passato un valore per riferimento a un operatore Windows Runtime o CLR definito dall'utente.  Se il valore viene modificato nella funzione, si noti che al valore restituito dopo la chiamata alla funzione verrà assegnato il valore restituito della funzione.  In C\+\+ standard, il valore modificato viene applicato dopo la chiamata alla funzione.  
  
## Esempio  
 L'esempio seguente genera l'errore C4460 e mostra come risolverlo.  
  
```  
// C4460.cpp  
// compile with: /W4 /clr   
#include <stdio.h>  
  
public value struct V {  
   static V operator ++(V& me) {   // C4460  
   // try the following line instead  
   // static V operator ++(V me) {  
  
      printf_s(__FUNCSIG__ " called\n");  
      V tmp = me;  
      me.m_i++;  
      return tmp;  
   }  
   int m_i;  
};  
  
int main() {  
   V v;  
   v.m_i = 0;  
  
   printf_s("%d\n", v.m_i);   // Should print 0  
   v++;   // Translates to "v = V::operator ++(v)"  
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning  
}  
```