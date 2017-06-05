---
title: "Definizioni di argomenti | Microsoft Docs"
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
  - "argc (argomento)"
  - "argomenti [C++], main (funzione)"
  - "argv (argomento)"
  - "envp (argomento)"
  - "main (funzione), argomenti"
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Definizioni di argomenti
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Gli argomenti nel prototipo  
  
```  
  
int main( int argc[ , char *argv[ ] [, char *envp[ ] ] ] ); int wmain( int argc[ , wchar_t *argv[ ] [, wchar_t *envp[ ] ] ] );  
```  
  
 consentono di eseguire l'utile analisi della riga di comando di argomenti e, facoltativamente, di accedere alle variabili di ambiente.  Le definizioni degli argomenti sono le seguenti:  
  
 `argc`  
 Un intero contenente il numero di argomenti che seguono in `argv`.  Il parametro `argc` è sempre maggiore di o uguale a 1.  
  
 `argv`  
 Una matrice di stringhe con terminazione null che rappresentano gli argomenti della riga di comando immessi dall'utente del programma.  Per convenzione, `argv`**\[0\]** è il comando con cui il programma viene richiamato, `argv`**\[1\]** è il primo argomento della riga di comando e così via fino a `argv`**\[**`argc`**\]**, che è sempre **NULL**.  Per informazioni sull'eliminazione dell'elaborazione della riga di comando, vedere [Personalizzazione dell'elaborazione della riga di comando](../cpp/customizing-cpp-command-line-processing.md).  
  
 Il primo argomento della riga di comando è sempre `argv`**\[1\]** e l'ultimo è `argv`**\[**`argc` \- 1**\]**.  
  
> [!NOTE]
>  Per convenzione, `argv`**\[0\]** è il comando con cui il programma viene richiamato.  Tuttavia, è possibile generare un processo utilizzando [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) e, se si utilizza sia il primo che il secondo argomento, \(`lpApplicationName` e `lpCommandLine`\), `argv`**\[0\]** non può essere il nome eseguibile; utilizzare [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) per recuperare il nome eseguibile e il relativo percorso completo.  
  
## Sezione specifica Microsoft  
 `envp`  
 La matrice `envp`, che è un'estensione comune in molti sistemi UNIX, viene utilizzata in Microsoft C\+\+.  È una matrice di stringhe che rappresentano le variabili impostate nell'ambiente dell'utente.  Questa matrice viene terminata da una voce **NULL**.  Può essere dichiarata come matrice di puntatori a **char \(char** \*envp\[ \]**\)** o come puntatore a puntatori a **char \(char** \*\* envp**\)**.  Se il programma utilizza **wmain** anziché **main**, utilizzare il tipo di dati `wchar_t` anziché `char`.  Il blocco di ambiente viene passato a **main** e **wmain** è una copia "bloccata" dell'ambiente corrente.  Se successivamente si modifica l'ambiente tramite una chiamata a **putenv** o a `_wputenv`, l'ambiente corrente \(come restituito da `getenv`\/`_wgetenv` e la variabile `_wenviron` \/ `_environ`\) cambia, ma il blocco che fa riferimento a envp rimane invariato.  Per informazioni sull'eliminazione dell'elaborazione dell'ambiente, vedere [Personalizzazione dell'elaborazione della riga di comando](../cpp/customizing-cpp-command-line-processing.md).  Questo argomento è compatibile con ANSI in C, ma non in C\+\+.  
  
## Fine sezione specifica Microsoft  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare gli argomenti `argc`, `argv` e `envp` per **main**:  
  
```  
// argument_definitions.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
int main( int argc, char *argv[], char *envp[] ) {  
    int iNumberLines = 0;    // Default is no line numbers.  
  
    // If /n is passed to the .exe, display numbered listing  
    // of environment variables.  
  
    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )  
         iNumberLines = 1;  
  
    // Walk through list of strings until a NULL is encountered.  
    for( int i = 0; envp[i] != NULL; ++i ) {  
        if( iNumberLines )  
            cout << i << ": " << envp[i] << "\n";  
    }  
}  
```  
  
## Vedere anche  
 [main: avvio del programma](../cpp/main-program-startup.md)