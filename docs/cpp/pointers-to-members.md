---
title: "Puntatori a membri | Microsoft Docs"
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
  - "membri di classi, puntatori"
  - "dichiarazioni, puntatori"
  - "membri, puntatori"
  - "puntatori, dichiarazioni"
  - "puntatori, a membri"
ms.assetid: f42ddb79-9721-4e39-95b1-c56b55591f68
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Puntatori a membri
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Le dichiarazioni dei puntatori ai membri sono casi speciali di dichiarazioni del puntatore.  Le funzioni vengono dichiarate tramite la seguente sequenza:  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [ms-modifier]  
qualified-name ::* [cv-qualifiers] identifier  
[= & qualified-name :: member-name];  
```  
  
1.  Identificatore di dichiarazione:  
  
    -   Identificatore della classe di archiviazione facoltativo.  
  
    -   Identificatori **const** e\/o `volatile` opzionali.  
  
    -   Il tipo di identificatore: il nome di un tipo.  Questo è il tipo del membro a cui puntare, non la classe.  
  
2.  Dichiaratore:  
  
    -   Un modificatore facoltativo specifico di Microsoft.  Per altre informazioni, vedere il sito Web Microsoft [Modificatori specifici di Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
    -   Il nome completo della classe che contiene i membri a cui puntare.  Vedere [Nomi e nomi completi](../misc/names-and-qualified-names.md).  
  
    -   Operatore ::.  
  
    -   Operatore **\***.  
  
    -   Identificatori **const** e\/o `volatile` opzionali.  
  
    -   L'identificatore di denominazione del puntatore a membro.  
  
    -   Inizializzatore facoltativo:  
  
 Operatore **\=**.  
  
 Operatore **&**.  
  
 Nome completo della classe.  
  
 Operatore `::`.  
  
 Il nome di un membro non statico della classe del tipo appropriato.  
  
 Come sempre, più dichiaratori \(e tutti gli inizializzatori associati\) sono consentiti in una singola dichiarazione.  
  
 Un puntatore a un membro di una classe differisce da un puntatore normale perché contiene informazioni per il tipo di membro e per la classe a cui appartiene il membro.  Un puntatore normale identifica \(con l'indirizzo\) un singolo oggetto in memoria.  Un puntatore a un membro di una classe identifica tale membro in qualsiasi istanza della classe.  Nell'esempio seguente viene dichiarata una classe, `Window`, e alcuni puntatori ai dati dei membri.  
  
```  
// pointers_to_members1.cpp  
class Window  
{  
public:  
   Window();                               // Default constructor.  
   Window( int x1, int y1,                 // Constructor specifying  
   int x2, int y2 );                       //  window size.  
bool SetCaption( const char *szTitle ); // Set window caption.  
   const char *GetCaption();               // Get window caption.  
   char *szWinCaption;                     // Window caption.  
};  
  
// Declare a pointer to the data member szWinCaption.  
char * Window::* pwCaption = &Window::szWinCaption;  
int main()  
{  
}  
```  
  
 Nell'esempio precedente, `pwCaption` è un puntatore a un membro di classe `Window` di tipo **char\***.  Il tipo di `pwCaption` è `char * Window::*`.  Il frammento di codice seguente dichiara i puntatori alle funzioni membro `SetCaption` e `GetCaption`.  
  
```  
const char * (Window::*pfnwGC)() = &Window::GetCaption;  
bool (Window::*pfnwSC)( const char * ) = &Window::SetCaption;  
```  
  
 I puntatori `pfnwGC` e `pfnwSC` puntano a `GetCaption` e `SetCaption` della classe `Window`, rispettivamente.  Il codice copia informazioni nella didascalia della finestra direttamente tramite il puntatore a membro `pwCaption`:  
  
```  
Window wMainWindow;  
Window *pwChildWindow = new Window;  
char   *szUntitled    = "Untitled -  ";  
int    cUntitledLen   = strlen( szUntitled );  
  
strcpy_s( wMainWindow.*pwCaption, cUntitledLen, szUntitled );  
(wMainWindow.*pwCaption)[cUntitledLen - 1] = '1';     //same as  
//wMainWindow.SzWinCaption [cUntitledLen - 1] = '1';  
strcpy_s( pwChildWindow->*pwCaption, cUntitledLen, szUntitled );   
(pwChildWindow->*pwCaption)[cUntitledLen - 1] = '2'; //same as //pwChildWindow->szWinCaption[cUntitledLen - 1] = '2';  
```  
  
 La differenza tra gli operatori **.\*** e **–\>\*** \(gli operatori puntatore a membro\) consiste nel fatto che l'operatore **.\*** seleziona i membri secondo un oggetto o un riferimento a un oggetto fornito, mentre l'operatore **–\>\*** seleziona i membri tramite un puntatore.  \(Per altre informazioni su questi operatori, vedere [Espressioni con gli operatori puntatore a membro](../cpp/pointer-to-member-operators-dot-star-and-star.md)\).  
  
 Il risultato dell'operatore puntatore a membro è il tipo del membro \(in questo caso, **char \***\).  
  
 Il frammento di codice seguente richiama le funzioni membro `GetCaption` e `SetCaption` tramite puntatori a membri:  
  
```  
// Allocate a buffer.  
enum {  
    sizeOfBuffer = 100  
};  
char szCaptionBase[sizeOfBuffer];  
  
// Copy the main window caption into the buffer  
//  and append " [View 1]".  
strcpy_s( szCaptionBase, sizeOfBuffer, (wMainWindow.*pfnwGC)() );  
strcat_s( szCaptionBase, sizeOfBuffer, " [View 1]" );  
// Set the child window's caption.  
(pwChildWindow->*pfnwSC)( szCaptionBase );  
```  
  
## Limitazioni sui puntatori ai membri  
 L'indirizzo di un membro statico non è un puntatore a un membro.  È un normale puntatore all'istanza del membro statico.  Poiché una sola istanza di un membro statico è disponibile per tutti gli oggetti di una classe specificata, è possibile usare gli operatori address\-of **\(&\)** e dereference **\(\*\)**.  
  
## Puntatori a membri e funzioni virtuali  
 Il richiamo di una funzione virtuale tramite una funzione puntatore a membro funziona come se la funzione sia stata chiamata direttamente; la funzione corretta viene individuata nella v\- table e viene richiamata.  
  
 La chiave per le funzioni virtuali in esecuzione, come sempre, le richiama tramite un puntatore a una classe base.  \(Per altre informazioni sulle funzioni virtuali, vedere [Funzioni virtuali](../cpp/virtual-functions.md)\).  
  
 Nel codice seguente viene illustrato come richiamare una funzione virtuale con una funzione puntatore a membro:  
  
```  
// virtual_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Base  
{  
public:  
virtual void Print();  
};  
void (Base ::* bfnPrint)() = &Base :: Print;  
void Base :: Print()  
{  
cout << "Print function for class Base\n";  
}  
  
class Derived : public Base  
{  
public:  
void Print();  // Print is still a virtual function.  
};  
  
void Derived :: Print()  
{  
cout << "Print function for class Derived\n";  
}  
  
int main()  
{  
    Base   *bPtr;  
    Base    bObject;  
Derived dObject;  
bPtr = &bObject;    // Set pointer to address of bObject.  
(bPtr->*bfnPrint)();  
bPtr = &dObject;    // Set pointer to address of dObject.  
(bPtr->*bfnPrint)();  
}  
  
//Output: Print function for class Base  
Print function for class Derived  
```  
  
## Vedere anche  
 [Dichiaratori astratti C\+\+](http://msdn.microsoft.com/it-it/e7e18c18-0cad-4450-942b-d27e1d4dd088)