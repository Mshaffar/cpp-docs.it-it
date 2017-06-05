---
title: _aligned_free | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _aligned_free
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
- aligned_free
- _aligned_free
dev_langs:
- C++
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
caps.latest.revision: 16
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
ms.openlocfilehash: 8ddc662a1d497a419ebbaf0a93bfbf0ec17b664a
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="alignedfree"></a>_aligned_free
Libera un blocco di memoria che è stato allocato con [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) o [_aligned_offset_malloc](../../c-runtime-library/reference/aligned-offset-malloc.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
void _aligned_free (  
   void *memblock  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `memblock`  
 Puntatore al blocco di memoria che è stato restituito alla funzione `_aligned_malloc` o `_aligned_offset_malloc`.  
  
## <a name="remarks"></a>Note  
 `_aligned_free` è contrassegnato `__declspec(noalias)`, pertanto si garantisce che la funzione non modifichi le variabili globali. Per altre informazioni, vedere [noalias](../../cpp/noalias.md).  
  
 Questa funzione non convalida il parametro, a differenza di altre funzioni CRT _aligned. Se `memblock` è un puntatore `NULL`, questa funzione non esegue alcuna azione. Non modifica `errno` e non richiama il gestore di parametri non validi. Se si verifica un errore nella funzione a causa del mancato utilizzo precedente di funzioni _aligned per allocare il blocco di memoria oppure si verifica un problema di allineamento della memoria a causa di alcune calamità impreviste, la funzione genera un report di debug dalle [Macro _RPT, _RPTF, _RPTW, _RPTFW](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md).  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`_aligned_free`|\<malloc.h>|  
  
## <a name="example"></a>Esempio  
 Per altre informazioni, vedere [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Allineamento dati](../../c-runtime-library/data-alignment.md)