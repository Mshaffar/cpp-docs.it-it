---
title: "Operatori puntatore a membro: .* e -&gt;* | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - ".*"
  - "->*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".* (operatore)"
  - "->* (operatore)"
  - "espressioni [C++], operatori"
  - "espressioni [C++], puntatore"
  - "operatori puntatore a membro"
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operatori puntatore a membro: .* e -&gt;*
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintassi  
  
```  
  
      expression .* expression  
expression –>* expression  
```  
  
## Note  
 Gli operatori puntatore a membro .\* e \-\>\* restituiscono il valore di un membro della classe specifico per l'oggetto indicato a sinistra dell'espressione.  Nella parte destra deve essere specificato un membro della classe.  Nell'esempio seguente viene illustrato come utilizzare tali operatori.  
  
```  
// expre_Expressions_with_Pointer_Member_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
class Testpm {  
public:  
   void m_func1() { cout << "m_func1\n"; }  
   int m_num;  
};  
  
// Define derived types pmfn and pmd.  
// These types are pointers to members m_func1() and  
// m_num, respectively.  
void (Testpm::*pmfn)() = &Testpm::m_func1;  
int Testpm::*pmd = &Testpm::m_num;  
  
int main() {  
   Testpm ATestpm;  
   Testpm *pTestpm = new Testpm;  
  
// Access the member function  
   (ATestpm.*pmfn)();  
   (pTestpm->*pmfn)();   // Parentheses required since * binds  
                        // less tightly than the function call.  
  
// Access the member data  
   ATestpm.*pmd = 1;  
   pTestpm->*pmd = 2;  
  
   cout  << ATestpm.*pmd << endl  
         << pTestpm->*pmd << endl;  
   delete pTestpm;  
}  
```  
  
## Output  
  
```  
m_func1  
m_func1  
1  
2  
```  
  
 Nell'esempio precedente un puntatore a un membro, `pmfn`, viene utilizzato per richiamare la funzione membro `m_func1`.  Un altro puntatore a un membro, `pmd`, viene utilizzato per accedere al membro `m_num`.  
  
 L'operatore binario .\* associa il proprio primo operando, che deve essere un oggetto di tipo classe, con il secondo operando, che deve essere di tipo puntatore a membro.  
  
 L'operatore binario –\>\* associa il proprio primo operando, che deve essere un puntatore a un oggetto di tipo classe, con il secondo operando, che deve essere di tipo puntatore a membro.  
  
 In un'espressione che contiene l'operatore .\* il primo operando deve essere del tipo di classe del puntatore a membro specificato nel secondo operando \(e deve essere accessibile da tale puntatore\) o di un tipo accessibile senza ambiguità derivato da e accessibile da tale classe.  
  
 In un'espressione che contiene l'operatore –\>\* il primo operando deve essere del tipo "puntatore al tipo di classe" del tipo specificato nel secondo operando o di un tipo derivato senza ambiguità da tale classe.  
  
## Esempio  
 Considerare le classi e il frammento di programma seguenti:  
  
```  
// expre_Expressions_with_Pointer_Member_Operators2.cpp  
// C2440 expected  
class BaseClass {  
public:  
   BaseClass(); // Base class constructor.  
   void Func1();  
};  
  
// Declare a pointer to member function Func1.  
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;  
  
class Derived : public BaseClass {  
public:  
   Derived();  // Derived class constructor.  
   void Func2();  
};  
  
// Declare a pointer to member function Func2.  
void (Derived::*pmfnFunc2)() = &Derived::Func2;  
  
int main() {  
   BaseClass ABase;  
   Derived ADerived;  
  
   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.  
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to  
                           // access pointers to members of  
                           // derived classes.   
  
   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously  
                              // derived from BaseClass.   
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.  
}  
```  
  
 Il risultato degli operatori puntatore a membro .\* o –\>\* è un oggetto o una funzione del tipo specificato nella dichiarazione del puntatore a membro.  Nell'esempio precedente il risultato dell'espressione `ADerived.*pmfnFunc1()` è un puntatore a una funzione che restituisce un valore nullo.  Questo risultato è un valore l\-value se il secondo operando è un valore di questo tipo.  
  
> [!NOTE]
>  Se il risultato di uno degli operatori puntatore a membro è una funzione, il risultato può essere utilizzato solo come operando dell'operatore di chiamata di funzione.  
  
## Vedere anche  
 [Operatori C\+\+](../misc/cpp-operators.md)   
 [Operatori C\+\+, precedenza e associazione](../cpp/cpp-built-in-operators-precedence-and-associativity.md)