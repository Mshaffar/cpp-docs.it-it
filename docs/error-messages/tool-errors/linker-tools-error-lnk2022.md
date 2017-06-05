---
title: Strumenti del linker LNK2022 errore | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2022
dev_langs:
- C++
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 6f12c53d7dd1383ad8f994a713c7226ab038cb19
ms.contentlocale: it-it
ms.lasthandoff: 04/01/2017

---
# <a name="linker-tools-error-lnk2022"></a>Errore degli strumenti del linker LNK2022
operazione sui metadati non riuscita (HRESULT): error_message  
  
 Il linker ha rilevato un errore durante l'unione dei metadati. Per collegare correttamente, è necessario risolvere gli errori di metadati.  
  
 Un modo per diagnosticare questo problema consiste nell'eseguire **ildasm-token** sui file per trovare tipi di oggetto sono elencati i token in `error_message`ed esaminare le differenze.  Nei metadati, due tipi diversi con lo stesso nome non è valido, anche se l'attributo LayoutType è diverso.  
  
 Per LNK2022 è quando un tipo (ad esempio, uno struct) presente in più moduli con lo stesso nome ma con definizioni in conflitto, e quando si compila con [/clr](../../build/reference/clr-common-language-runtime-compilation.md).  In questo caso, assicurarsi che il tipo ha una definizione identica in tutti i moduli.  Il nome del tipo è elencato nella `error_message`.  
  
 Un'altra possibile causa LNK2022 è quando il linker rileva un file di metadati in un percorso diverso rispetto a quello indicato al compilatore (con [#using](../../preprocessor/hash-using-directive-cpp.md) ). Assicurarsi che il file metadati (con estensione dll o netmodule), quando viene passato al linker, si trovi nello stesso percorso di quando è stato passato al compilatore.  
  
 Quando si compila un'applicazione ATL, l'utilizzo di [_ATL_MIXED è presente](http://msdn.microsoft.com/Library/11b59a83-7098-43e2-9f7b-408299930966) è obbligatorio in tutti i moduli, se viene utilizzato in almeno uno.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente definisce un tipo vuoto.  
  
```  
// LNK2022_a.cpp  
// compile with: /clr /c  
public ref class Test {};  
```  
  
## <a name="example"></a>Esempio  
 Questo esempio viene illustrato che è possibile collegare i due file di codice sorgente che contengono i tipi con lo stesso nome ma definizioni diverse.  
  
 L'esempio seguente genera l'errore LNK2022.  
  
```  
// LNK2022_b.cpp  
// compile with: LNK2022_a.cpp /clr /LD   
// LNK2022 expected  
public ref class Test {  
   void func() {}  
   int var;  
};  
```