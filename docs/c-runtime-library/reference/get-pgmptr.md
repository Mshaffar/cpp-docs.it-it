---
title: _get_pgmptr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _get_pgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_pgmptr
- _get_pgmptr
dev_langs:
- C++
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: bb04c82492a241c8a1089e2414358a11b54fff70
ms.contentlocale: it-it
ms.lasthandoff: 04/04/2017

---
# <a name="getpgmptr"></a>_get_pgmptr
Ottiene il valore corrente della variabile globale `_pgmptr`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
errno_t _get_pgmptr(   
   char **pValue   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 [out] `pValue`  
 Puntatore a una stringa in cui inserire il valore corrente della variabile `_pgmptr`.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce zero se ha esito positivo; un codice di errore se ha esito negativo. Se `pValue` è `NULL`, viene richiamato il gestore di parametri non validi, come descritto in [Convalida dei parametri](../../c-runtime-library/parameter-validation.md). Se l'esecuzione può continuare, la funzione imposta `errno` su`EINVAL` e restituisce `EINVAL`.  
  
## <a name="remarks"></a>Note  
 Il `_pgmptr` (variabile globale) contiene il percorso completo del file eseguibile associato al processo. Per altre informazioni, vedere [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`_get_pgmptr`|\<stdlib.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibility](../../c-runtime-library/compatibility.md) (Compatibilità) nell'introduzione.  
  
## <a name="see-also"></a>Vedere anche  
 [_get_wpgmptr](../../c-runtime-library/reference/get-wpgmptr.md)