---
title: "Avviso del compilatore (livello 4) C4625 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4625"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4625"
ms.assetid: 4cc99e50-846c-4784-97da-48b977067851
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Avviso del compilatore (livello 4) C4625
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'derived class': il costruttore di copia è stato definito in modo implicito come eliminato perché un costruttore di copia della classe di base è inaccessibile o è stato eliminato  
  
 Un costruttore di copia è stato eliminato o non è accessibile in una classe di base e quindi non è stato generato per una classe derivata.  Qualsiasi tentativo di copiare un oggetto di questo tipo causerà un errore del compilatore.  
  
 Per impostazione predefinita, questo avviso non è attivo.  Per altre informazioni, vedere [Avvisi del compilatore disattivati per impostazione predefinita](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Esempio  
 L'esempio seguente genera l'errore C4625 e mostra come risolverlo.  
  
```  
// C4625.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4625)  
  
struct A {  
   A() {}  
  
private:  
   A(const A&) {}  
};  
  
struct C : private virtual A {};  
struct B :  C {};   // C4625 no copy constructor  
  
struct D : A {};  
struct E :  D {};   // OK  
```