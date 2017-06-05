---
title: "Funzioni virtuali | Microsoft Docs"
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
  - "classi derivate, funzioni virtual"
  - "funzioni [C++], funzioni virtual"
  - "funzioni virtual"
ms.assetid: b3e1ed88-2a90-4af8-960a-16f47deb3452
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Funzioni virtuali
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una funzione virtuale è una funzione membro che si prevede venga ridefinita nelle classi derivate.  Quando si fa riferimento a un oggetto della classe derivata usando un puntatore o un riferimento alla classe base, è possibile chiamare una funzione virtuale per quell'oggetto ed eseguire la versione della classe derivata della funzione.  
  
 Con le funzioni virtuali viene assicurata la chiamata della funzione corretta per un oggetto, indipendentemente dall'espressione usata per effettuare la chiamata di funzione.  
  
 Si supponga che una classe base contenga una funzione dichiarata come [vituale](../cpp/virtual-cpp.md) e una classe derivata definisca la stessa funzione.  La funzione della classe derivata viene richiamata per gli oggetti della classe derivata, anche se viene chiamata mediante un puntatore o un riferimento alla classe base.  Nell'esempio seguente viene illustrata una classe base che fornisce un'implementazione della funzione `PrintBalance` e delle due classi derivate.  
  
```  
// deriv_VirtualFunctions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Account {  
public:  
   Account( double d ) { _balance = d; }  
   virtual double GetBalance() { return _balance; }  
   virtual void PrintBalance() { cerr << "Error. Balance not available for base type." << endl; }  
private:  
    double _balance;  
};  
  
class CheckingAccount : public Account {  
public:  
   CheckingAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Checking account balance: " << GetBalance() << endl; }  
};  
  
class SavingsAccount : public Account {  
public:  
   SavingsAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Savings account balance: " << GetBalance(); }  
};  
  
int main() {  
   // Create objects of type CheckingAccount and SavingsAccount.  
   CheckingAccount *pChecking = new CheckingAccount( 100.00 ) ;  
   SavingsAccount  *pSavings  = new SavingsAccount( 1000.00 );  
  
   // Call PrintBalance using a pointer to Account.  
   Account *pAccount = pChecking;  
   pAccount->PrintBalance();  
  
   // Call PrintBalance using a pointer to Account.  
   pAccount = pSavings;  
   pAccount->PrintBalance();     
}  
```  
  
 Nel codice precedente le chiamate a `PrintBalance` sono identiche, a eccezione dell'oggetto a cui fa riferimento `pAccount`.  Poiché `PrintBalance` è virtuale, viene chiamata la versione della funzione definita per ogni oggetto.  La funzione `PrintBalance` nelle classi derivate `CheckingAccount` e `SavingsAccount` "esegue l'override" della funzione presente nella classe base `Account`.  
  
 Se una classe dichiarata non fornisce un'implementazione di override della funzione `PrintBalance`, viene usata l'implementazione predefinita della classe base `Account`.  
  
 Le funzioni nelle classi derivate eseguono l'override delle funzioni virtuali nelle classi base solo se il relativo tipo è lo stesso.  Una funzione in una classe derivata non può essere diversa da una funzione virtuale in una classe base solo nel tipo restituito; pure l'elenco di argomenti deve essere diverso.  
  
 Nel chiamare una funzione usando i puntatori o riferimenti, vengono applicate le seguenti regole:  
  
-   Una chiamata a una funzione virtuale viene risolta in base al tipo sottostante di oggetto per il quale viene chiamato.  
  
-   Una chiamata a una funzione non virtuale viene risolta in base al tipo del puntatore o di riferimento.  
  
 Di seguito viene illustrato un esempio del modo in cui funzioni virtuali e non virtuali si comportano una volta chiamate tramite puntatori:  
  
```  
// deriv_VirtualFunctions2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Base {  
public:  
   virtual void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Base::NameOf() {  
   cout << "Base::NameOf\n";  
}  
  
void Base::InvokingClass() {  
   cout << "Invoked by Base\n";  
}  
  
class Derived : public Base {  
public:  
   void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Derived::NameOf() {  
   cout << "Derived::NameOf\n";  
}  
  
void Derived::InvokingClass() {  
   cout << "Invoked by Derived\n";  
}  
  
int main() {  
   // Declare an object of type Derived.  
   Derived aDerived;  
  
   // Declare two pointers, one of type Derived * and the other  
   //  of type Base *, and initialize them to point to aDerived.  
   Derived *pDerived = &aDerived;  
   Base    *pBase    = &aDerived;  
  
   // Call the functions.  
   pBase->NameOf();           // Call virtual function.  
   pBase->InvokingClass();    // Call nonvirtual function.  
   pDerived->NameOf();        // Call virtual function.  
   pDerived->InvokingClass(); // Call nonvirtual function.  
}  
```  
  
### Output  
  
```  
Derived::NameOf  
Invoked by Base  
Derived::NameOf  
Invoked by Derived  
```  
  
 Si noti che la funzione `NameOf` viene chiamata per `Base` sia se viene richiamata tramite un puntatore a `Derived` sia se viene richiamata tramite un puntatore a `Derived`.  La funzione viene chiamata per `Derived` poiché `NameOf` è una funzione virtuale e `pBase` e `pDerived` puntano a un oggetto di tipo `Derived`.  
  
 Poiché le funzioni virtuali vengono chiamate per oggetti di tipi di classe, non è possibile dichiarare funzioni globali o statiche come **virtual**.  
  
 La parola chiave **virtual** può essere usata per le dichiarazioni di funzioni di override in una classe derivata, ma non è necessaria; le esecuzioni di override di funzioni virtuali sono sempre virtuali.  
  
 Le funzioni virtuali in una classe base devono essere definite a meno che non vengano dichiarate usando *pure\-specifier*.  Per altre informazioni sulle classi astratte, vedere [Classi astratte](../cpp/abstract-classes-cpp.md).  
  
 Il meccanismo virtuale di chiamata di funzione può essere eliminato in modo esplicito specificando il nome di funzione usando l'operatore di risoluzione dell'ambito \(`::`\).  Si consideri l'esempio precedente relativo alla classe `Account`.  Per chiamare `PrintBalance` nella classe base, usare codice simile al seguente:  
  
```  
CheckingAccount *pChecking = new CheckingAccount( 100.00 );  
  
pChecking->Account::PrintBalance();  //  Explicit qualification.  
  
Account *pAccount = pChecking;  // Call Account::PrintBalance  
  
pAccount->Account::PrintBalance();   //  Explicit qualification.  
```  
  
 Entrambe le chiamate a `PrintBalance` nell'esempio precedente eliminano il meccanismo di chiamata di funzione virtuale.  
  
## Vedere anche  
 [Accesso a funzioni virtuali](../misc/access-to-virtual-functions.md)