---
title: "Differenze nella gestione eccezioni | Microsoft Docs"
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
  - "gestione delle eccezioni di C++, e gestione eccezioni strutturata"
  - "eccezioni, classe wrapper"
  - "gestione eccezioni strutturata, e gestione delle eccezioni di C++"
  - "gestione eccezioni strutturata, e non strutturata"
  - "classi wrapper, eccezione C"
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Differenze nella gestione eccezioni
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La differenza principale tra gestione delle eccezioni strutturata e gestione delle eccezioni C\+\+ è che il modello di gestione delle eccezioni C\+\+ gestisce i tipi, mentre il modello di gestione delle eccezioni strutturata di C gestisce le eccezioni di un solo tipo \(in particolare, `unsigned int`\).  In altre parole, le eccezioni C sono identificate da un intero senza segno, mentre le eccezioni C\+\+ sono identificate dal tipo di dati.  Quando viene generata un'eccezione in C, ogni possibile gestore esegue un filtro che esamina il contesto di eccezione C e determina se accettare l'eccezione, passarla a un altro gestore o ignorarla.  Quando viene generata un'eccezione in C\+\+, può essere di qualsiasi tipo.  
  
 Un'altra differenza consiste nel fatto che il modello di gestione delle eccezioni strutturata di C è denominato "asincrono" poiché le eccezioni sono secondarie al flusso di controllo normale.  Il meccanismo di gestione delle eccezioni C\+\+ è totalmente "sincrono" che significa che le eccezioni si verificano solo quando vengono generate.  
  
 Se un'eccezione C viene generata in un programma C\+\+, può essere gestita da un gestore di eccezioni strutturato con il filtro associato o da un gestore **catch** C\+\+, a seconda di quale si trova dinamicamente più vicino al contesto di eccezione.  Ad esempio, il seguente programma C\+\+ genera un'eccezione C nel contesto **try** di C \+\+:  
  
## Esempio  
  
```  
// exceptions_Exception_Handling_Differences.cpp  
// compile with: /EHa  
#include <iostream>  
  
using namespace std;  
void SEHFunc( void );  
  
int main() {  
   try {  
      SEHFunc();  
   }  
   catch( ... ) {  
      cout << "Caught a C exception."<< endl;  
   }  
}  
  
void SEHFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
   }  
   __finally {  
      cout << "In finally." << endl;  
   }  
}  
```  
  
  **In finally.**  
**Rilevata un'eccezione C.**   
##  <a name="_core_c_exception_wrapper_class"></a> Classe wrapper di eccezione C  
 In un esempio semplice come il precedente, l'eccezione C può essere rilevata solo da un gestore **catch** con i puntini di sospensione \(**...**\).  Nessuna informazione sul tipo o la natura dell'eccezione viene comunicata al gestore.  Quando viene utilizzato questo metodo, in alcuni casi, potrebbe essere necessario definire una trasformazione tra i due modelli di gestione delle eccezioni in modo da associare ogni eccezione C a una classe specifica.  A tale scopo, è possibile definire la classe "wrapper" di eccezione C che può essere utilizzata o da cui può essere derivata per associare un tipo di classe specifico a un'eccezione C.  In tal modo, ogni eccezione C può essere gestita da un gestore **catch** C\+\+ più separatamente che nell'esempio precedente.  
  
 La classe wrapper potrebbe avere un'interfaccia composta da alcune funzioni membro che determinano il valore dell'eccezione e che accedono alle informazioni sul contesto delle eccezioni estese fornite dal modello di eccezione C.  È inoltre possibile definire un costruttore predefinito, un costruttore che accetta un argomento `unsigned int` \(per fornire la rappresentazione dell'eccezione C sottostante\) e un costruttore di copia bit per bit.  Di seguito è riportata una possibile implementazione di una classe wrapper di eccezione C:  
  
```  
// exceptions_Exception_Handling_Differences2.cpp  
// compile with: /c  
class SE_Exception {  
private:  
   SE_Exception() {}  
   SE_Exception( SE_Exception& ) {}  
   unsigned int nSE;  
public:  
   SE_Exception( unsigned int n ) : nSE( n ) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() {  
      return nSE;  
   }  
};  
  
```  
  
 Per utilizzare questa classe, si installa una funzione di conversione di eccezione C personalizzata definita dal meccanismo interno di gestione delle eccezioni ogni volta che viene generata un'eccezione.  All'interno della funzione di conversione, è possibile generare qualsiasi eccezione tipizzata \(probabilmente un tipo `SE_Exception` o un tipo di classe derivato da `SE_Exception`\) intercettabile da un appropriato gestore **catch** C\+\+ corrispondente.  La funzione di conversione può eseguire semplicemente una restituzione che indica che l'eccezione non è stata gestita.  Se la stessa funzione di conversione genera un'eccezione C, viene chiamata la funzione [termine](../c-runtime-library/reference/terminate-crt.md).  
  
 Per specificare una funzione di conversione personalizzata, chiamare la funzione [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md) con il nome della funzione di conversione come unico argomento.  La funzione di conversione che si scrive viene chiamata una volta per ogni chiamata di funzione nello stack con blocchi **try**.  Non esiste una funzione di conversione predefinita; se non se ne specifica una chiamando `_set_se_translator`, l'eccezione C può essere rilevata solo da un gestore **catch** con i puntini di sospensione.  
  
## Esempio  
 Ad esempio, il codice riportato di seguito installa una funzione di conversione personalizzata, quindi genera un'eccezione C di cui viene eseguito il wrapping nella classe `SE_Exception`:  
  
```  
// exceptions_Exception_Handling_Differences3.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <eh.h>  
#include <windows.h>  
  
class SE_Exception {  
private:  
   SE_Exception() {}  
   unsigned int nSE;  
  
public:  
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}  
   SE_Exception(unsigned int n) : nSE(n) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() { return nSE; }  
};  
  
void SEFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
    }  
    __finally {  
      printf_s( "In finally\n" );  
   }  
}  
  
void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {  
   printf_s( "In trans_func.\n" );  
   throw SE_Exception( u );  
}  
  
int main() {  
   _set_se_translator( trans_func );  
    try {  
      SEFunc();  
    }  
    catch( SE_Exception e ) {  
      printf_s( "Caught a __try exception with SE_Exception.\n" );  
      printf_s( "nSE = 0x%x\n", e.getSeNumber() );  
    }  
}  
```  
  
  **In trans\_func.**  
**In finally**  
**Rilevata un'eccezione \_\_try con SE\_Exception.**  
**nSE \= 0xc0000094**   
## Vedere anche  
 [Combinazione di eccezioni C \(strutturate\) ed eccezioni C\+\+](../cpp/mixing-c-structured-and-cpp-exceptions.md)