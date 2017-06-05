---
title: "Modelli e risoluzione di nomi | Microsoft Docs"
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
ms.assetid: 519ba7b5-cd25-4549-865a-9a7b9dffdc28
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Modelli e risoluzione di nomi
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Nelle definizioni di modello esistono tre tipi di nomi.  
  
-   I nomi dichiarati a livello locale, incluso il nome del modello stesso e i nomi dichiarati all'interno della definizione di modello.  
  
-   Nomi provenienti dall'ambito che li contiene al di fuori della definizione di modello.  
  
-   Nomi che dipendono in qualche modo dagli argomenti di modello, noti come nomi dipendente.  
  
 Mentre i primi due tipi di nomi appartengono agli ambiti della classe e della funzione, sono necessarie regole speciali per la risoluzione dei nomi nelle definizioni di modelli, per gestire la complessità aggiuntiva dei nomi dipendente.  Questo perché il compilatore dispone di pochissime informazioni su questi nomi fino a quando non viene creata un'istanza del modello, in quanto potrebbero essere tipi completamente diversi in base agli argomenti di modello utilizzati.  I nomi non dipendente vengono ricercati in base alle regole usuali e al punto di definizione del modello.  Questi nomi, essendo indipendenti dagli argomenti di modello, vengono ricercati una sola volta per tutte le specializzazioni del modello.  I nomi dipendente non vengono ricercati fino a quando non viene creata un'istanza del modello e vengono ricercati separatamente per ogni specializzazione.  
  
 Un tipo è dipendente se dipende dagli argomenti di modello.  In particolare, un tipo è dipendente se è:  
  
-   L'argomento del modello stesso:  
  
    ```  
    T  
    ```  
  
-   Un nome completo con una qualificazione incluso un tipo dipendente:  
  
    ```  
    T::myType  
    ```  
  
-   Un nome completo se la parte non completa identifica un tipo dipendente:  
  
    ```  
    N::T  
    ```  
  
-   Un tipo const o volatile per il quale il tipo di base è un tipo dipendente:  
  
    ```  
    const T  
    ```  
  
-   Un puntatore, un riferimento, una matrice o un tipo puntatore a funzione basato su un tipo dipendente:  
  
    ```  
    T *, T &, T [10], T (*)()  
    ```  
  
-   Una matrice le cui dimensioni sono basate su un parametro di modello:  
  
    ```  
    template <int arg> class X {  
    int x[arg] ; // dependent type  
    }  
    ```  
  
-   Un tipo di modello costruito da un parametro di modello:  
  
    ```  
    T<int>, MyTemplate<T>  
    ```  
  
## Dipendenza di tipo e dipendenza di valore  
 I nomi e le espressioni dipendenti da un parametro di modello sono classificati come dipendente di tipo o dipendente di valore, a seconda se il parametro di modello è un parametro di tipo o un parametro di valore.  Inoltre, tutti gli identificatori dichiarati in un modello con un dipendente di tipo nell'argomento del modello sono considerati dipendente di valore, così come lo è un tipo integrale o di enumerazione inizializzato con un'espressione dipendente di valore.  
  
 Le espressioni dei dipendenti di tipo e dei dipendenti di valore sono espressioni che includono variabili che sono dipendente di tipo o dipendente di valore.  Queste espressioni possono avere semantiche differenti a seconda dei parametri utilizzati per il modello.  
  
## Vedere anche  
 [Modelli](../cpp/templates-cpp.md)