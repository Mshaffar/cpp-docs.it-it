---
title: _mbccpy, _mbccpy_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbccpy
- _mbccpy_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbccpy
- tccpy
- ftccpy
- mbccpy
- _tccpy
- _ftccpy
dev_langs:
- C++
helpviewer_keywords:
- _tccpy function
- _tccpy_l function
- tccpy_l function
- tccpy function
- mbccpy function
- _mbccpy_l function
- _mbccpy function
- mbccpy_l function
ms.assetid: 13f4de6e-7792-41ac-b319-dd9b135433aa
caps.latest.revision: 24
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
ms.openlocfilehash: a2c085e754e43e0909552a68d36b8393708cf7ac
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="mbccpy-mbccpyl"></a>_mbccpy, _mbccpy_l
Copia un carattere multibyte da una stringa in un'altra stringa. Sono disponibili versioni più sicure di queste funzioni. Vedere [_mbccpy_s, _mbccpy_s_l](../../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md).  
  
> [!IMPORTANT]
>  Non è possibile usare questa API nelle applicazioni eseguite in Windows Runtime. Per altre informazioni, vedere l'articolo relativo alle [funzioni CRT non supportate con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintassi  
  
```  
void _mbccpy(  
   unsigned char *dest,  
   const unsigned char *src   
);  
void _mbccpy_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dest`  
 Destinazione della copia.  
  
 `src`  
 Caratteri multibyte da copiare.  
  
 `locale`  
 Impostazioni locali da usare.  
  
## <a name="remarks"></a>Note  
 La funzione `_mbccpy` copia un carattere multibyte da `src` a `dest`.  
  
 Questa funzione convalida i relativi parametri. Se alla funzione `_mbccpy` viene passato un puntatore Null per `dest` o `src`, viene richiamato il gestore di parametri non validi, come descritto in [Convalida dei parametri](../../c-runtime-library/parameter-validation.md). Se l'esecuzione può continuare, `errno` viene impostato su `EINVAL`.  
  
 `_mbccpy` usa le impostazioni locali correnti per qualsiasi comportamento dipendente dalle impostazioni locali. La funzione `_mbccpy_l` è identica a `_mbccpy`, ma `_mbccpy_l` usa le impostazioni locali passate per qualsiasi comportamento dipendente dalle impostazioni locali. Per altre informazioni, vedere [Impostazioni locali](../../c-runtime-library/locale.md).  
  
 **Nota sulla sicurezza** Usare una stringa con terminazione Null. Le dimensioni della stringa con terminazione Null non devono essere superiori a quelle del buffer di destinazione. Per altre informazioni, vedere [Evitare sovraccarichi del buffer](http://msdn.microsoft.com/library/windows/desktop/ms717795). I problemi di sovraccarico del buffer sono usati spesso come metodo di attacco di sistema e provocano un'elevazione dei privilegi non autorizzata.  
  
### <a name="generic-text-routine-mappings"></a>Mapping di routine di testo generico  
  
|Routine Tchar.h|_UNICODE e _MBCS non definiti|_MBCS definito|_UNICODE definito|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tccpy`|Mapping a una macro o a una funzione inline|`_mbccpy`|Mapping a una macro o a una funzione inline|  
|`_tccpy_l`|n/d|`_mbccpy_l`|n/d|  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`_mbccpy`|\<mbctype.h>|  
|`_mbccpy_l`|\<mbctype.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni locali](../../c-runtime-library/locale.md)   
 [Interpretazione di sequenze di caratteri multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)