---
title: _fread_nolock_s2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _fread_nolock_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fread_nolock_s
- stdio/_fread_nolock_s
dev_langs:
- C++
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
caps.latest.revision: 3
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: f7f6dff1902777d5c795ac5cb29e1bcfdf3b0eb5
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="freadnolocks"></a>_fread_nolock_s
Legge i dati da un flusso senza bloccare altri thread. Questa versione di [fread_nolock](../../c-runtime-library/reference/fread-nolock.md) include miglioramenti per la sicurezza, come descritto in [Funzionalità di sicurezza in CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
size_t _fread_nolock_s(   
   void *buffer,  
   size_t bufferSize,  
   size_t elementSize,  
   size_t elementCount,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `buffer`  
 Percorso di archiviazione per i dati.  
  
 `bufferSize`  
 Dimensioni del buffer di destinazione in byte.  
  
 `elementSize`  
 Dimensione dell'elemento da leggere in byte.  
  
 `elementCount`  
 Numero massimo di elementi da leggere.  
  
 `stream`  
 Puntatore alla struttura `FILE` .  
  
## <a name="return-value"></a>Valore restituito  
 Vedere [fread_s](../../c-runtime-library/reference/fread-s.md).  
  
## <a name="remarks"></a>Note  
 Questa funzione è una versione non di blocco di `fread_s`. È identica a `fread_s` con la differenza che non è protetta da interferenze da parte di altri thread. Potrebbe essere più veloce perché non comporta un sovraccarico che blocca altri thread. Utilizzare questa funzione solo in contesti thread-safe come applicazioni a thread singolo o dove l'ambito chiamante già gestisce l'isolamento del thread.  
  
## <a name="requirements"></a>Requisiti  
  
|Funzione|Intestazione obbligatoria|  
|--------------|---------------------|  
|`_fread_nolock_s`|C: \<stdio.h>; C++: \<cstdio> o \<stdio.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibility](../../c-runtime-library/compatibility.md) (Compatibilità) nell'introduzione.  
  
## <a name="see-also"></a>Vedere anche  
 [I/O di flusso](../../c-runtime-library/stream-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [_read](../../c-runtime-library/reference/read.md)