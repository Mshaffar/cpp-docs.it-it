---
title: "Funzioni che restituiscono tipi di riferimento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipi di dati [C++], tipi restituiti dalla funzione"
  - "tipi restituiti dalla funzione, tipo di riferimento"
  - "funzioni [C++], tipi restituiti"
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Funzioni che restituiscono tipi di riferimento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

È possibile dichiarare le funzioni affinché restituiscano un tipo di riferimento.  La dichiarazione di una funzione viene effettuata per due motivi:  
  
-   Le informazioni da restituire sono un oggetto di dimensioni abbastanza grandi da far sì che la restituzione di un riferimento risulti più efficiente rispetto alla restituzione di una copia.  
  
-   Il tipo di funzione deve essere un l\-value.  
  
-   L'oggetto a cui si fa riferimento non uscirà dall'ambito al completamento della funzione.  
  
 Come può essere più efficiente passare oggetti di grandi dimensioni *alle* funzioni per riferimento, può essere più efficiente anche restituire oggetti di grandi dimensioni *dalle* funzioni con questo metodo.  Il protocollo riferimento\-restituzione elimina la necessità di copiare l'oggetto in un percorso temporaneo prima della restituzione.  
  
 I tipi riferimento\-restituzione possono rivelarsi utili quando la funzione deve restituire un l\-value.  La maggior parte degli operatori di overload rientra in questa categoria, in particolare l'operatore di assegnazione.  Gli operatori di overload sono illustrati in [Operatori di overload](../cpp/operator-overloading.md).  
  
## Esempio  
 Considerare l'esempio `Point`:  
  
```  
// refType_function_returns.cpp  
// compile with: /EHsc  
  
#include <iostream>  
using namespace std;  
  
class Point  
{  
public:  
// Define "accessor" functions as  
//  reference types.  
unsigned& x();  
unsigned& y();  
private:  
// Note that these are declared at class scope:  
unsigned obj_x;   
unsigned obj_y;   
};  
  
unsigned& Point :: x()  
{  
return obj_x;  
}  
unsigned& Point :: y()  
{  
return obj_y;  
}  
  
int main()  
{  
Point ThePoint;  
// Use x() and y() as l-values.  
ThePoint.x() = 7;  
ThePoint.y() = 9;  
  
// Use x() and y() as r-values.  
cout << "x = " << ThePoint.x() << "\n"  
<< "y = " << ThePoint.y() << "\n";  
}  
```  
  
## Output  
  
```  
x = 7  
y = 9  
```  
  
 Tenere presente che le funzioni `x` e `y` vengono dichiarate come elementi che restituiscono tipi di riferimenti.  Tali funzioni possono essere usate su entrambi i lati di un'istruzione di assegnazione.  
  
 Si noti anche che in genere l'oggetto ThePoint rimane nell'ambito e quindi i rispettivi membri di riferimento sono ancora attivi ed è possibile accedervi in modo sicuro.  
  
 Le dichiarazioni di tipi di riferimenti devono contenere gli inizializzatori tranne nei seguenti casi:  
  
-   Dichiarazione `extern` esplicita  
  
-   Dichiarazione di un membro di classe  
  
-   Dichiarazione all'interno di una classe  
  
-   Dichiarazione di un argomento in una funzione o del tipo restituito da una funzione  
  
## Attenzione nella restituzione dell'indirizzo di una variabile locale  
 Se si dichiara un oggetto a livello di ambito locale, tale oggetto verrà eliminato al completamento della funzione.  Se la funzione restituisce un riferimento all'oggetto, tale riferimento provocherà probabilmente una violazione di accesso in fase di esecuzione se il chiamante tenta di usare il riferimento Null.  
  
```  
// C4172 means Don’t do this!!!  
Foo& GetFoo()  
{  
    Foo f;  
    ...  
    return f;  
} // f is destroyed here  
```  
  
 Il compilatore emette in avviso in questo caso: `warning C4172: returning address of local variable or temporary`.  Nei programmi semplici è possibile che occasionalmente non si verifichino violazioni di accesso se il chiamante accede al riferimento prima della sovrascrittura della posizione di memoria.  È una questione di fortuna.  È consigliabile prestare attenzione all'avviso.  
  
## Vedere anche  
 [Riferimenti](../cpp/references-cpp.md)