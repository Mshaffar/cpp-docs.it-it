---
title: _SCL_SECURE_NO_WARNINGS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs: C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c1a821fd86ab85a68c84f982d47351c6d08256de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS
Se si chiama uno dei metodi potenzialmente non sicuri inclusi nella libreria standard C++, verrà generato l'[Avviso del compilatore (livello 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Per disabilitare questo avviso, definire la macro **_SCL_SECURE_NO_WARNINGS** nel codice:  
  
```  
#define _SCL_SECURE_NO_WARNINGS  
```  
  
## <a name="remarks"></a>Note  
 Gli altri modi per disabilitare l'avviso C4996 includono:  
  
-   L'uso dell'opzione del compilatore [/D (definizioni preprocessore)](../build/reference/d-preprocessor-definitions.md):  
  
 ```  
    cl /D_SCL_SECURE_NO_WARNINGS [other compiler options] myfile.cpp  
```  
  
-   L'uso dell'opzione del compilatore [/w](../build/reference/compiler-option-warning-level.md):  
  
 ```  
    cl /wd4996 [other compiler options] myfile.cpp  
```  
  
-   L'uso di una direttiva [#pragma warning](../preprocessor/warning.md):  
  
 ```  
 #pragma warning(disable:4996)  
```  
  
 Inoltre, è possibile modificare manualmente il livello di avviso C4996 con il **/w\<l >\< n>**  l'opzione del compilatore. Ad esempio, per impostare l'avviso C4996 sul livello 4:  
  
```  
cl /w44996 [other compiler options] myfile.cpp  
```  
  
 Per altre informazioni, vedere [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Livello di avviso)](../build/reference/compiler-option-warning-level.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Librerie protette: libreria standard C++](../standard-library/safe-libraries-cpp-standard-library.md)
