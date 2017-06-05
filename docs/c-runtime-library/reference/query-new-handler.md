---
title: _query_new_handler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _query_new_handler
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _query_new_handler
- query_new_handler
dev_langs:
- C++
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
caps.latest.revision: 10
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
ms.openlocfilehash: 63d43e80009b0d6c8f2d827f6ea5b239d7a39663
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="querynewhandler"></a>_query_new_handler
Restituisce l'indirizzo della routine del nuovo gestore corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
_PNH _query_new_handler(  
   void   
);  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce l'indirizzo della routine del nuovo gestore corrente, come impostato da `_set_new_handler`.  
  
## <a name="remarks"></a>Note  
 La funzione C++ `_query_new_handler` restituisce l'indirizzo della funzione di gestione delle eccezioni corrente impostata dalla funzione C++ [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md). La funzione `_set_new_handler` viene usata per specificare una funzione di gestione delle eccezioni che deve assumere il controllo se l'operatore **new** non riesce ad allocare memoria. Per altre informazioni, vedere la discussione relativa agli [operatori new e delete](../../cpp/new-and-delete-operators.md) nelle informazioni di riferimento sul linguaggio C++.  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`_query_new_handler`|\<new.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md) nell'introduzione.  
  
## <a name="libraries"></a>Librerie  
 Tutte le versioni delle [librerie di runtime C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Allocazione di memoria](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)