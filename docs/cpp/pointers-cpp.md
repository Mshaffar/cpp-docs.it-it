---
title: "Puntatori | Microsoft Docs"
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
  - "dichiarazioni, puntatori"
  - "dichiaratori, puntatori"
  - "puntatori"
  - "puntatori, dichiarazioni"
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Puntatori
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

I puntatori vengono dichiarati tramite la seguente sequenza  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator ;  
```  
  
 Qui qualsiasi dichiaratore valido del puntatore può essere utilizzato per `declarator`.  La sintassi di un dichiaratore di puntatore semplice è la seguente:  
  
```  
* [cv-qualifiers] identifier [= expression]  
```  
  
 1.  Gli identificatori di dichiarazione:  
  
-   Identificatore della classe di archiviazione facoltativo.  Per ulteriori informazioni, vedere [Identificatori](../cpp/specifiers.md).  
  
-   Una parola chiave `const` o `volatile` facoltativa, applicata al tipo di oggetto a cui puntare.  
  
-   L'identificatore di tipo: il nome di un tipo che rappresenta il tipo di oggetto a cui puntare.  
  
 2.  Dichiaratore:  
  
-   Un modificatore facoltativo specifico di Microsoft.  Per ulteriori informazioni, vedere il sito Web Microsoft [Modificatori specifici di Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
-   Operatore `*`.  
  
-   Una parola chiave `const` o `volatile` facoltativa che si applica al puntatore stesso.  
  
-   Identificatore.  
  
-   Inizializzatore facoltativo.  
  
 Il dichiaratore per un puntatore a funzione ha il seguente aspetto:  
  
```  
(* [cv-qualifiers] identifier )( argument-list ) [cv-qualifers]  
[exception specification] [= expression];  
```  
  
-   La sintassi per una matrice di puntatori ha il seguente aspetto:  
  
```  
* identifier [ [ constant-expression ] ]  
```  
  
-   Tuttavia, i dichiaratori del puntatore possono essere più complessi.  Per ulteriori informazioni, vedere [Dichiaratori](http://msdn.microsoft.com/it-it/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838).  
  
-   Più dichiaratori e i relativi inizializzatori possono essere uniti in una sola dichiarazione in un elenco separato da virgola che segue l'identificatore della dichiarazione.  
  
 Un esempio semplice di dichiarazione di puntatore è:  
  
```  
char *pch;  
```  
  
 La dichiarazione precedente specifica che `pch` punta a un oggetto di tipo `char`.  
  
 Un esempio più complesso è  
  
```  
static unsigned int * const ptr;  
```  
  
 La dichiarazione precedente specifica che `ptr` è un puntatore costante a un oggetto di tipo `unsigned` `int` con durata di archiviazione statica.  
  
 L'esempio riportato di seguito mostra il modo in cui vengono dichiarati e inizializzati più puntatori:  
  
```  
static int *p = &i, *q = &j;  
```  
  
 Nell'esempio precedente i puntatori p e in q puntano entrambi a oggetti di tipo `int` e vengono inizializzati, rispettivamente sugli indirizzi di i e J.  L'identificatore della classe di archiviazione `static` viene applicato a entrambi i puntatori.  
  
## Esempio  
  
```  
// pointer.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   int i = 1, j = 2; // local variables on the stack  
   int *p;  
  
   // a pointer may be assigned to "point to" the value of  
   // another variable using the & (address of) operator  
   p = & j;   
  
   // since j was on the stack, this address will be somewhere  
   // on the stack.  Pointers are printed in hex format using  
   // %p and conventionally marked with 0x.    
   printf_s("0x%p\n",  p);  
  
   // The * (indirection operator) can be read as "the value  
   // pointed to by".  
   // Since p is pointing to j, this should print "2"  
   printf_s("0x%p %d\n",  p, *p);  
  
   // changing j will change the result of the indirection  
   // operator on p.  
   j = 7;  
   printf_s("0x%p %d\n",  p, *p );  
  
   // The value of j can also be changed through the pointer  
   // by making an assignment to the dereferenced pointer  
   *p = 10;  
   printf_s("j is %d\n", j); // j is now 10  
  
   // allocate memory on the heap for an integer,  
   // initialize to 5  
   p = new int(5);  
  
   // print the pointer and the object pointed to  
   // the address will be somewhere on the heap  
   printf_s("0x%p %d\n",  p, *p);  
  
   // free the memory pointed to by p  
   delete p;  
  
   // At this point, dereferencing p with *p would trigger  
   // a runtime access violation.  
  
   // Pointer arithmetic may be done with an array declared  
   // on the stack or allocated on the heap with new.  
   // The increment operator takes into account the size   
   // of the objects pointed to.  
   p = new int[5];  
   for (i = 0; i < 5; i++, p++) {  
      *p = i * 10;  
      printf_s("0x%p %d\n", p, *p);  
   }  
  
   // A common expression seen is dereferencing in combination  
   // with increment or decrement operators, as shown here.  
   // The indirection operator * takes precedence over the   
   // increment operator ++.   
   // These are particularly useful in manipulating char arrays.  
   char s1[4] = "cat";  
   char s2[4] = "dog";  
   char* p1 = s1;  
   char* p2 = s2;  
  
   // the following is a string copy operation  
   while (*p1++ = *p2++);  
  
   // s2 was copied into s1, so now they are both equal to "dog"  
   printf_s("%s %s", s1, s2);  
}  
```  
  
  **0x0012FEC8**  
**0x0012FEC8 2**  
**0x0012FEC8 7**  
**J è 10**  
**0x00320850 5**  
**0x00320850 0**  
**0x00320854 10**  
**0x00320858 20**  
**0x0032085C 30**  
**0x00320860 40**  
**dog dog**   
## Esempio  
 In un altro esempio viene illustrato l'utilizzo dei puntatori nelle strutture di dati; in questo caso, un elenco collegato.  
  
```  
// pointer_linkedlist.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct NewNode {  
   NewNode() : node(0){}  
   int i;  
   NewNode * node;  
};  
  
void WalkList(NewNode * ptr) {  
   if (ptr != 0) {  
      int i = 1;  
      while (ptr->node != 0 ) {  
         cout << "node " << i++ << " = " << ptr->i << endl;  
         ptr = ptr->node;  
      }  
      cout << "node " << i++ << " = " << ptr->i << endl;  
   }  
}  
  
void AddNode(NewNode ** ptr) {  
   NewNode * walker = 0;  
   NewNode * MyNewNode = new NewNode;  
   cout << "enter a number: " << endl;  
   cin >> MyNewNode->i;  
  
   if (*ptr == 0)  
      *ptr = MyNewNode;  
   else  {  
      walker = *ptr;  
      while (walker->node != 0)  
         walker = walker->node;  
  
      walker->node = MyNewNode;  
   }  
}  
  
int main() {  
   char ans = ' ';  
   NewNode * ptr = 0;  
   do {  
      cout << "a (add node)  d (display list)  q (quit)" << endl;  
      cin >> ans;  
      switch (ans) {  
      case 'a':  
         AddNode(&ptr);  
         break;  
      case 'd':  
         WalkList(ptr);  
         break;  
      }  
   } while (ans != 'q');  
}  
```  
  
  **`a 45 d a 789 d q`a \(add node\)  d \(display list\)  q \(quit\)**  
**enter a number:**   
**a \(add node\)  d \(display list\)  q \(quit\)**  
**node 1 \= 45**  
**a \(add node\)  d \(display list\)  q \(quit\)**  
**enter a number:**   
**a \(add node\)  d \(display list\)  q \(quit\)**  
**node 1 \= 45**  
**node 2 \= 789**  
**a \(add node\)  d \(display list\)  q \(quit\)**   
## Vedere anche  
 [C\+\+ Abstract Declarators](http://msdn.microsoft.com/it-it/e7e18c18-0cad-4450-942b-d27e1d4dd088)   
 [Aggiunta di tipi di puntatori](../misc/addition-of-pointer-types.md)   
 [Operatore di riferimento indiretto: \*](../cpp/indirection-operator-star.md)   
 [Operatore address\-of: &](../cpp/address-of-operator-amp.md)