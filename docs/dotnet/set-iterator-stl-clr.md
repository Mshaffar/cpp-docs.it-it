---
title: "set::iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator (membro) [STL/CLR]"
ms.assetid: 7e54276b-4cb3-4bff-a3a6-23ae328aa369
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# set::iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Il tipo di un iteratore della sequenza controllata.  
  
## Sintassi  
  
```  
typedef T1 iterator;  
```  
  
## Note  
 Il tipo viene descritto un oggetto di tipo non specificato `T1` che può essere utilizzata come iteratore bidirezionale per la sequenza selezionata.  
  
## Esempio  
  
```  
// cliext_set_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## Requisiti  
 **Intestazione:**\<cliext\/set\>  
  
 **Spazio dei nomi:** cliext  
  
## Vedere anche  
 [set](../dotnet/set-stl-clr.md)   
 [set::const\_iterator](../dotnet/set-const-iterator-stl-clr.md)