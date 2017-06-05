---
title: Errore del compilatore C3383 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3383
dev_langs:
- C++
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 57ff8d9694aa5cefbb3772fd0acca39c84011d6c
ms.contentlocale: it-it
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3383"></a>Errore del compilatore C3383
'operator new' non supportato con /clr:safe  
  
 Il file di output di una compilazione **/clr:safe** è un file indipendente dai tipi verificabile e i puntatori non sono supportati.  
  
 Per ulteriori informazioni, vedere,  
  
-   [/CLR (compilazione common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problemi comuni relativi alla migrazione di Visual C++ a 64 bit](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Esempio  
 L'esempio seguente genera l'errore C3383.  
  
```  
// C3383.cpp  
// compile with: /clr:safe  
int main() {  
   char* pCharArray = new char[256];  // C3383  
}  
```