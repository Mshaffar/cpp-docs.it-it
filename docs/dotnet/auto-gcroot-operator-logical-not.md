---
title: "auto_gcroot::operator! | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr.auto_gcroot.operator!"
  - "auto_gcroot.operator!"
  - "msclr::auto_gcroot::operator!"
  - "auto_gcroot::operator!"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto_gcroot::operator!"
ms.assetid: f9728be3-2e09-4c01-a594-43e0d59d40d3
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_gcroot::operator!
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Operatore per utilizzare `auto_gcroot` in un'espressione condizionale.  
  
## Sintassi  
  
```  
bool operator!() const;  
```  
  
## Valore restituito  
 `true` se l'oggetto di cui è stato eseguito il wrapping non è valido; `false` in caso contrario.  
  
## Esempio  
  
```  
// msl_auto_gcroot_operator_not.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
int main() {  
   auto_gcroot<String^> s;  
   if ( s ) Console::WriteLine( "s is valid" );  
   if ( !s ) Console::WriteLine( "s is invalid" );  
   s = "something";  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
   s.reset();  
   if ( s ) Console::WriteLine( "now s is valid" );  
   if ( !s ) Console::WriteLine( "now s is invalid" );  
}  
```  
  
  **s non è valida**  
**ora s è valida**  
**ora s non è valida**   
## Requisiti  
 msclr \<\\ auto\_gcroot.h di**File di intestazione** \>  
  
 msclr di**Spazio dei nomi**  
  
## Vedere anche  
 [Membri auto\_gcroot](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::operator bool](../dotnet/auto-gcroot-operator-bool.md)