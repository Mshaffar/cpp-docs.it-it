---
title: "Modelli di funzioni | Microsoft Docs"
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
  - "modelli di funzioni"
  - "modelli di funzioni, informazioni su modelli di funzioni"
  - "modelli, funzione"
ms.assetid: 59b56a4b-0689-4161-9c07-25021562e2a7
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Modelli di funzioni
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

I modelli di classe definiscono un gruppo di classi correlate, basate sugli argomenti di tipo passati alla classe mediante la creazione di istanze.  I modelli di funzione sono simili ai modelli di classe ma definiscono un gruppo di funzioni.  Con i modelli di funzione è possibile specificare un set di funzioni basate sullo stesso codice, ma che agiscono su tipi o classi differenti.  Il modello di funzione seguente scambia due elementi:  
  
```  
// function_templates1.cpp  
template< class T > void MySwap( T& a, T& b ) {  
   T c(a);   
   a = b;   
   b = c;  
}  
int main() {  
}  
```  
  
 Questo codice definisce un gruppo di funzioni che scambiano i valori degli argomenti.  Da questo modello è possibile generare funzioni che scambiano tipi `int` e **long** oltre che i tipi definiti dall'utente.  `MySwap` scambia anche le classi se il costruttore di copia e l'operatore di assegnazione della classe sono definiti correttamente.  
  
 Inoltre, il modello di funzione impedirà di scambiare oggetti di tipi diversi, poiché il compilatore riconosce i tipi dei parametri `b` e `a` in fase di compilazione.  
  
 Sebbene questa funzione possa essere eseguita da una funzione non basata su modelli, utilizzando i puntatori void, la versione del modello è indipendente dai tipi.  Considerare le chiamate seguenti:  
  
```  
int j = 10;  
int k = 18;  
CString Hello = "Hello, Windows!";  
MySwap( j, k );          //OK  
MySwap( j, Hello );      //error  
```  
  
 La seconda chiamata `MySwap` attiva un errore in fase di compilazione, in quanto il compilatore non può generare una funzione `MySwap` con parametri di tipi differenti.  Se sono stati utilizzati puntatori void, entrambe le chiamate di funzione verranno compilate correttamente, tuttavia la funzione non verrà eseguita nel modo previsto in fase di esecuzione.  
  
 La specifica esplicita degli argomenti di modelli per un modello di funzione non è consentita.  Ad esempio:  
  
```  
// function_templates2.cpp  
template<class T> void f(T) {}  
int main(int j) {  
   f<char>(j);   // Generate the specialization f(char).  
   // If not explicitly specified, f(int) would be deduced.  
}  
```  
  
 Quando un argomento di modello è specificato in modo esplicito, le normali conversioni implicite vengono effettuate per convertire l'argomento della funzione nel tipo dei parametri del modello di funzione corrispondente.  Nell'esempio precedente il compilatore converte \(`char j`\) nel tipo `int`.  
  
## Vedere anche  
 [Modelli](../cpp/templates-cpp.md)   
 [Creazione di istanze di modelli di funzione](../cpp/function-template-instantiation.md)   
 [Creazione di un'istanza esplicita](../cpp/explicit-instantiation.md)   
 [Specializzazione esplicita di modelli di funzioni](../cpp/explicit-specialization-of-function-templates.md)