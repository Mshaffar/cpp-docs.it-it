---
title: Macro _STATIC_ASSERT | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _STATIC_ASSERT
dev_langs:
- C++
helpviewer_keywords:
- _STATIC_ASSERT macro
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: 6
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 265796cdebbed1c0a067c44bbe6b71077be44a2b
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="staticassert-macro"></a>Macro _STATIC_ASSERT
Valutare un'espressione in fase di compilazione e generare un errore quando il risultato è `FALSE`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `booleanExpression`  
 Espressione (inclusi i puntatori) che restituisce un valore diverso da zero (`TRUE`) oppure 0 (`FALSE`).  
  
## <a name="remarks"></a>Note  
 Questa macro è simile alle [macro _ASSERT e _ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), con la differenza che `booleanExpression` viene valutato in fase di compilazione anziché in fase di esecuzione. Se `booleanExpression` restituisce `FALSE` (0), viene generato l'[errore del compilatore C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md).  
  
## <a name="example"></a>Esempio  
 In questo esempio, controlliamo se `sizeof` `int` è maggiore o uguale a 2 byte e se `sizeof` `long` è di 1 byte. Il programma non verrà compilato e genererà l'[errore del compilatore C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md) perché un valore `long` è maggiore di 1 byte.  
  
```  
// crt__static_assert.c  
  
#include <crtdbg.h>  
#include <stdio.h>  
  
_STATIC_ASSERT(sizeof(int) >= 2);  
_STATIC_ASSERT(sizeof(long) == 1);  // C2466  
  
int main()  
{  
    printf("I am sure that sizeof(int) will be >= 2: %d\n",  
        sizeof(int));  
    printf("I am not so sure that sizeof(long) == 1: %d\n",  
        sizeof(long));  
}  
```  
  
## <a name="requirements"></a>Requisiti  
  
|Macro|Intestazione obbligatoria|  
|-----------|---------------------|  
|`_STATIC_ASSERT`|\<crtdbg.h>|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alfabetico alle funzioni](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Macro _ASSERT, _ASSERTE, _ASSERT_EXPR](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)