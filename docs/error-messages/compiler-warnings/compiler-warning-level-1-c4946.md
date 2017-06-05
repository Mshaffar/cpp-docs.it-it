---
title: "Avviso del compilatore (livello 1) C4946 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4946"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4946"
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Avviso del compilatore (livello 1) C4946
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

reinterpret\_cast utilizzato tra le classi correlate 'classe1' e 'classe2'  
  
 Non utilizzare [reinterpret\_cast](../../cpp/reinterpret-cast-operator.md) per eseguire il cast tra tipi correlati.  Utilizzare [static\_cast](../../cpp/static-cast-operator.md) invece, o per tipi polimorfici, utilizzare [dynamic\_cast](../../cpp/dynamic-cast-operator.md).  
  
 Per impostazione predefinita, questo avviso non è attivo.  Per ulteriori informazioni, vedere [Avvisi del compilatore disattivati per impostazione predefinita](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Nell'esempio riportato di seguito il codice genera l'errore C4946:  
  
```  
// C4946.cpp  
// compile with: /W1  
#pragma warning (default : 4946)  
class a {  
public:  
   a() : m(0) {}  
   int m;  
};  
  
class b : public virtual a {  
};  
  
class b2 : public virtual a {  
};  
  
class c : public b, public b2 {  
};  
  
int main() {  
   c* pC = new c;  
   a* pA = reinterpret_cast<a*>(pC);   // C4946  
   // try the following line instead  
   // a* pA = static_cast<a*>(pC);  
}  
```