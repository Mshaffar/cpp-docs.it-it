---
title: "Ambito (Visual C++) | Microsoft Docs"
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
  - "ambito classe"
  - "classi [C++], ambito"
  - "prototipi di funzioni, ambito"
  - "funzioni [C++], ambito"
  - "ambito prototipo"
  - "ambito"
  - "ambito, nomi C++"
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ambito (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

I nomi in C\+\+ possono essere usati solo in alcune aree del programma.  Quest'area viene denominata "l'ambito" del nome.  L'ambito determina la "durata" di un nome che non indica un oggetto con estensione statica.  L'ambito determina inoltre la visibilità di un nome quando vengono chiamati i costruttori e i distruttori di classe e quando vengono inizializzate le variabili locali per l'ambito.  Per altre informazioni, vedere [Costruttori](../cpp/constructors-cpp.md) e [Distruttori](../cpp/destructors-cpp.md). Esistono cinque tipi di ambito:  
  
-   **Ambito locale** Un nome dichiarato in un blocco è accessibile solo all'interno di tale blocco e dei blocchi da esso racchiusi e solo dopo la dichiarazione.  I nomi degli argomenti formali di una funzione nell'ambito del relativo blocco più esterno hanno ambito locale, come se fossero stati dichiarati all'interno del blocco che racchiude il corpo della funzione.  Si consideri il frammento di codice riportato di seguito.  
  
    ```  
    {  
        int i;  
    }  
    ```  
  
     Poiché la dichiarazione di `i` si trova in un blocco racchiuso tra parentesi graffe, `i` ha ambito locale e non è mai accessibile perché nessun codice vi accede prima della parentesi graffa chiusa.  
  
-   **Ambito funzione** Le etichette sono gli unici nomi che dispongono dell'ambito funzione.  Possono essere usate in qualsiasi punto di una funzione, ma non sono accessibili all'esterno della stessa funzione.  Gli argomenti formali delle funzioni, ovvero argomenti specificati nelle definizioni di funzione, sono considerati nell'ambito del blocco più esterno del corpo della funzione.  
  
-   **Ambito file** Qualsiasi nome dichiarato all'esterno di tutti i blocchi o di tutte le classi dispone di un ambito file.  È accessibile da qualsiasi punto dell'unità di conversione dopo la relativa dichiarazione.  I nomi con ambito file che non dichiarano oggetti statici vengono spesso denominati nomi globali.  
  
     In C\+\+, l'ambito file è anche noto come ambito dello spazio dei nomi.  
  
-   **Ambito di classe** I nomi dei membri di classe dispongono dell'ambito di classe.  Le funzioni membro delle classi sono accessibili solo tramite gli operatori di selezione dei membri \(**.** o **–\>**\) oppure gli operatori puntatore a membro \(**.\*** o **–\>\***\) in un oggetto o in un puntatore a un oggetto di tale classe; i dati dei membri di classe non statici vengono considerati locali rispetto all'oggetto di tale classe.  Si consideri la seguente dichiarazione di classe:  
  
    ```  
    class Point  
    {  
        int x;  
        int y;  
    };  
    ```  
  
     I membri della classe `x` e `y` vengono considerati nell'ambito della classe `Point`.  
  
-   **Ambito prototipo** I nomi dichiarati in un prototipo di funzione sono visibili solo fino alla fine di tale prototipo.  Il prototipo riportato di seguito dichiara tre nomi \(`strDestination`, `numberOfElements` e `strSource`\); questi nomi escono dall'ambito alla fine del prototipo:  
  
    ```  
    errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
    ```  
  
## Nascondere nomi  
 È possibile nascondere un nome dichiarandolo in un blocco chiuso.  Nella figura seguente `i` viene ridichiarato nel blocco interno, quindi nascondendo la variabile associata a `i` nell'ambito blocco esterno.  
  
 ![Nascondere il nome dell'ambito blocco](../cpp/media/vc38sf1.png "vc38SF1")  
Nascondere il nome e l'ambito blocco  
  
 L'output del programma illustrato nella figura è:  
  
```  
i = 0  
i = 7  
j = 9  
i = 0  
```  
  
> [!NOTE]
>  L'argomento `szWhat` viene considerato nell'ambito della funzione.  Di conseguenza, viene considerato come se fosse stato dichiarato nel blocco più esterno della funzione.  
  
## Nascondere nomi di classi  
 È possibile nascondere i nomi della classe mediante la dichiarazione di una funzione, un oggetto o una variabile o un enumeratore nello stesso ambito.  Tuttavia, l'accesso al nome della classe può ancora essere eseguito quando è preceduto dalla parola chiave **class**.  
  
```  
// hiding_class_names.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// Declare class Account at file scope.  
class Account  
{  
public:  
    Account( double InitialBalance )  
        { balance = InitialBalance; }  
    double GetBalance()  
        { return balance; }  
private:  
    double balance;  
};  
  
double Account = 15.37;            // Hides class name Account  
  
int main()  
{  
    class Account Checking( Account ); // Qualifies Account as   
                                       //  class name  
  
    cout << "Opening account with balance of: "  
         << Checking.GetBalance() << "\n";  
}  
//Output: Opening account with balance of: 15.37  
```  
  
> [!NOTE]
>  Indipendentemente dalla posizione in cui viene chiamato il nome della classe \(`Account`\), la parole chiave class deve essere usata per differenziarla dalla variabile Account in ambito file.  Questa regola non viene applicata quando il nome della classe si trova a sinistra dell'operatore di risoluzione dell'ambito \(::\).  I nomi a sinistra dell'operatore di risoluzione dell'ambito vengono sempre considerati nomi classe.  
  
 Nell'esempio seguente viene illustrato come dichiarare un puntatore a un oggetto di tipo `Account` usando la parola chiave **class**:  
  
```  
class Account *Checking = new class Account( Account );  
```  
  
 L'elemento `Account` nell'inizializzatore \(tra parentesi\) nell'istruzione precedente dispone di un ambito file; è di tipo **double**.  
  
> [!NOTE]
>  Il riutilizzo dei nomi degli identificatori come illustrato in questo esempio viene considerato uno stile di programmazione di qualità insufficiente.  
  
 Per altre informazioni sui puntatori, vedere [Tipi derivati](http://msdn.microsoft.com/it-it/aa14183c-02fe-4d81-95fe-beddb0c01c7c).  Per informazioni sulla dichiarazione e inizializzazione di oggetti classe, vedere [Classi, strutture e unioni](../cpp/classes-and-structs-cpp.md).  Per informazioni su come usare gli operatori free\-store **new** e **delete**, vedere [Funzioni membro speciali](../misc/special-member-functions-cpp.md).  
  
## Nascondere nomi con ambito file  
 È possibile nascondere i nomi con ambito file dichiarando in modo esplicito lo stesso nome in ambito blocco.  È possibile accedere ai nomi di ambito file, però, usando l'operatore di risoluzione dell'ambito \(`::`\).  
  
```  
// file_scopes.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int i = 7;   // i has file scope, outside all blocks  
using namespace std;  
  
int main( int argc, char *argv[] ) {  
   int i = 5;   // i has block scope, hides i at file scope  
   cout << "Block-scoped i has the value: " << i << "\n";  
   cout << "File-scoped i has the value: " << ::i << "\n";  
}  
```  
  
  **Valore di i con ambito blocco: 5**  
**Valore di i con ambito file: 7**   
## Vedere anche  
 [Concetti di base](../cpp/basic-concepts-cpp.md)