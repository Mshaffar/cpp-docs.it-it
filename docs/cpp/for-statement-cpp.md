---
title: "Istruzione for (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for (parola chiave) [C++]"
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Istruzione for (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esegue ripetutamente un'istruzione finché la condizione non diventa false.  Per informazioni sull'istruzione for basata su intervallo, vedere [Istruzione for basata su intervallo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md).  
  
## Sintassi  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## Note  
 Utilizzare l'istruzione `for` per costruire cicli che dovranno essere eseguiti un numero specificato di volte.  
  
 L'istruzione `for` è costituita da tre parti facoltative, come illustrato nella tabella seguente.  
  
### Elementi del ciclo For  
  
|Nome della sintassi|Quando viene eseguito|Descrizione|  
|-------------------------|---------------------------|-----------------|  
|`init-expression`|Prima di qualsiasi altro elemento dell'istruzione **For**, `init-expression` viene eseguito una volta sola.  Il controllo passa a `cond-expression`.|Spesso utilizzato per inizializzare gli indici del ciclo.  Può contenere espressioni o dichiarazioni.|  
|`cond-expression`|Prima dell'esecuzione di ogni iterazione di `statement`, inclusa la prima iterazione.  `statement` viene eseguito solo se `cond-expression` restituisce true \(diverso da zero\).|Un'espressione che restituisce un tipo di classe o un tipo integrale con una conversione non ambigua a un tipo integrale.  Normalmente utilizzato per verificare i criteri di terminazione del ciclo For.|  
|`loop-expression`|Alla fine di ogni iterazione di `statement`.  Dopo l'esecuzione di `loop-expression`, viene valutato `cond-expression`.|Normalmente utilizzato per incrementare gli indici del ciclo.|  
  
 Negli esempi riportati di seguito vengono illustrati modi diversi per utilizzare l'istruzione `for`.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    // The counter variable can be declared in the init-expression.  
    for (int i = 0; i < 2; i++ ){   
       cout << i;  
    }  
    // Output: 01  
    // The counter variable can be declared outside the for loop.  
    int i;  
    for (i = 0; i < 2; i++){  
        cout << i;  
    }  
    // Output: 01  
    // These for loops are the equivalent of a while loop.  
    i = 0;  
    while (i < 2){  
        cout << i++;  
    }  
}  
    // Output: 012  
```  
  
 `init-expression` e `loop-expression` possono contenere più istruzioni separate da virgole.  Di seguito è riportato un esempio.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
    int i, j;  
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {  
        cout << "i + j = " << (i + j) << '\n';  
    }  
}  
    // Output:  
    i + j = 15  
    i + j = 17  
    i + j = 19  
```  
  
 `loop-expression` può essere incrementato o ridotto oppure modificato in altri modi.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
for (int i = 10; i > 0; i--) {  
        cout << i << ' ';  
    }  
    // Output: 10 9 8 7 6 5 4 3 2 1  
    for (int i = 10; i < 20; i = i+2) {  
        cout << i << ' ';  
    }  
    // Output: 10 12 14 16 18  
```  
  
 Un ciclo `for` termina con l'esecuzione di [break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md) o [goto](../cpp/goto-statement-cpp.md) \(a un'istruzione con etichetta all'esterno del ciclo **for**\) all'interno di `statement`.  Un'istruzione [continue](../cpp/continue-statement-cpp.md) in un ciclo `for` termina solo l'iterazione corrente.  
  
 Se `cond-expression` viene omesso, viene considerato true e il ciclo **For** verrà terminato senza `break`, `return` o `goto` all'interno di `statement`.  
  
 Sebbene i tre campi dell'istruzione `for` vengano in genere utilizzati per l'inizializzazione, la verifica della terminazione e l'incremento, non sono limitati a questi utilizzi.  Ad esempio, il codice seguente consente di stampare i numeri da 0 a 4.  In questo caso, `statement` è l'istruzione Null:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    int i;  
    for( i = 0; i < 5; cout << i << '\n', i++){  
        ;  
    }  
}  
```  
  
## per i cicli e lo standard C\+\+  
 Lo standard C\+\+ specifica che una variabile dichiarata in un ciclo `for` uscirà dall'ambito dopo la terminazione del ciclo `for`.  Di seguito è riportato un esempio.  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 Per impostazione predefinita, in [\/Ze](../build/reference/za-ze-disable-language-extensions.md), una variabile dichiarata in un ciclo `for` rimane nell'ambito finché non termina l'ambito che la contiene del ciclo `for`.  
  
 [\/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) consente il comportamento standard delle variabili dichiarate nei cicli For senza la necessità di specificare \/Za.  
  
 È anche possibile utilizzare le differenze di ambito del ciclo `for` per dichiarare nuovamente le variabili in \/Ze come segue:  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 Questo è molto simile al comportamento standard di una variabile dichiarata in un ciclo `for`, che richiede variabili dichiarate in un ciclo `for` per uscire dall'ambito al termine del ciclo.  Quando una variabile viene dichiarata in un ciclo `for`, il compilatore la promuove internamente a una variabile locale nell'ambito che la contiene del ciclo `for`, anche se esiste già una variabile locale con lo stesso nome.  
  
## Vedere anche  
 [Istruzioni di iterazione](../cpp/iteration-statements-cpp.md)   
 [Parole chiave C\+\+](../cpp/keywords-cpp.md)   
 [Istruzione while \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [Istruzione do\-while \(C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [Istruzione for basata su intervallo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)