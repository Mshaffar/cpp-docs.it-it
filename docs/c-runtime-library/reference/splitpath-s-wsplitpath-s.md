---
title: _splitpath_s, _wsplitpath_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wsplitpath_s
- _splitpath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
dev_langs:
- C++
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: 29
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
ms.openlocfilehash: c4c6803731deba188a4f4dba118b04f626f58564
ms.contentlocale: it-it
ms.lasthandoff: 04/04/2017

---
# <a name="splitpaths-wsplitpaths"></a>_splitpath_s, _wsplitpath_s
Suddivide un nome di percorso nei componenti. Queste sono versioni di [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md) con miglioramenti per la sicurezza, come descritto in [Funzionalità di sicurezza in CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
errno_t _splitpath_s(  
   const char * path,  
   char * drive,  
   size_t driveNumberOfElements,  
   char * dir,  
   size_t dirNumberOfElements,  
   char * fname,  
   size_t nameNumberOfElements,  
   char * ext,   
   size_t extNumberOfElements  
);  
errno_t _wsplitpath_s(  
   const wchar_t * path,  
   wchar_t * drive,  
   size_t driveNumberOfElements,  
   wchar_t *dir,  
   size_t dirNumberOfElements,  
   wchar_t * fname,  
   size_t nameNumberOfElements,  
   wchar_t * ext,  
   size_t extNumberOfElements  
);  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _splitpath_s(  
   const char *path,  
   char (&drive)[drivesize],  
   char (&dir)[dirsize],  
   char (&fname)[fnamesize],  
   char (&ext)[extsize]  
); // C++ only  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _wsplitpath_s(  
   const wchar_t *path,  
   wchar_t (&drive)[drivesize],  
   wchar_t (&dir)[dirsize],  
   wchar_t (&fname)[fnamesize],  
   wchar_t (&ext)[extsize]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametri  
 [in] `path`  
 Percorso completo.  
  
 [out] `drive`  
 Lettera di unità, seguita da due punti (`:`). È possibile passare `NULL` per questo parametro se non è necessaria la lettera di unità.  
  
 [in] `driveNumberOfElements`  
 Dimensioni del buffer `drive` in caratteri a byte singolo o wide. Se `drive` è `NULL`, questo valore deve essere 0.  
  
 [out] `dir`  
 Percorso di directory, inclusa la barra finale. È possibile usare barre ( `/` ), barre rovesciate ( `\` ) o entrambe. È possibile passare `NULL` per questo parametro se non è necessario il percorso di directory.  
  
 [in] `dirNumberOfElements`  
 Dimensioni del buffer `dir` in caratteri a byte singolo o wide. Se `dir` è `NULL`, questo valore deve essere 0.  
  
 [out] `fname`  
 Nome di file di base (senza estensione). È possibile passare `NULL` per questo parametro se non è necessario il nome di file.  
  
 [in] `nameNumberOfElements`  
 Dimensioni del buffer `fname` in caratteri a byte singolo o wide. Se `fname` è `NULL`, questo valore deve essere 0.  
  
 [out] `ext`  
 Estensione del nome di file, incluso il punto iniziale (**.**). È possibile passare `NULL` per questo parametro se non è necessaria l'estensione del nome di file.  
  
 [in] `extNumberOfElements`  
 Dimensioni del buffer `ext` in caratteri a byte singolo o wide. Se `ext` è `NULL`, questo valore deve essere 0.  
  
## <a name="return-value"></a>Valore restituito  
 Zero se con esito positivo; un codice di errore in caso di errore.  
  
### <a name="error-conditions"></a>Condizioni di errore  
  
|Condizione|Valore restituito|  
|---------------|------------------|  
|`path` è `NULL`|`EINVAL`|  
|`drive` è `NULL`, `driveNumberOfElements` è diverso da zero|`EINVAL`|  
|`drive` non è `NULL`, `driveNumberOfElements` è zero|`EINVAL`|  
|`dir` è `NULL`, `dirNumberOfElements` è diverso da zero|`EINVAL`|  
|`dir` non è `NULL`, `dirNumberOfElements` è zero|`EINVAL`|  
|`fname` è `NULL`, `nameNumberOfElements` è diverso da zero|`EINVAL`|  
|`fname` non è `NULL`, `nameNumberOfElements` è zero|`EINVAL`|  
|`ext` è `NULL`, `extNumberOfElements` è diverso da zero|`EINVAL`|  
|`ext` non è `NULL`, `extNumberOfElements` è zero|`EINVAL`|  
  
 Se si verifica una delle condizioni precedenti, viene richiamato il gestore di parametri non validi, come descritto in [Convalida dei parametri](../../c-runtime-library/parameter-validation.md). Se l'esecuzione può continuare, queste funzioni impostano `errno` su `EINVAL` e restituiscono `EINVAL`.  
  
 Se uno qualsiasi dei buffer è troppo breve per contenere il risultato, queste funzioni cancellano tutti i buffer per svuotarli dalle stringhe, impostano `errno` su `ERANGE` e restituiscono `ERANGE`.  
  
## <a name="remarks"></a>Note  
 La funzione `_splitpath_s` suddivide un percorso nei suoi quattro componenti. `_splitpath_s` gestisce automaticamente e in modo appropriato gli argomenti stringa di caratteri multibyte, riconoscendo le sequenze di caratteri multibyte in base alla tabella codici multibyte attualmente in uso. `_wsplitpath_s` è una versione a caratteri "wide" di `_splitpath_s`. Gli argomenti per `_``wsplitpath_s` sono stringhe a caratteri "wide". A parte ciò, queste funzioni si comportano in modo identico.  
  
### <a name="generic-text-routine-mappings"></a>Mapping di routine di testo generico  
  
|Routine TCHAR.H|_UNICODE e _MBCS non definiti|_MBCS definito|_UNICODE definito|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 Ogni componente del percorso completo è archiviata in un buffer separato. Le costanti manifeste `_MAX_DRIVE`, `_MAX_DIR`, `_MAX_FNAME` e `_MAX_EXT` (definite in STDLIB.H) specificano le dimensioni massime consentite per ogni componente del file. I componenti del file più grandi delle costanti manifeste corrispondenti causano il danneggiamento dell'heap.  
  
 La tabella seguente elenca i valori delle costanti manifeste.  
  
|Nome|Valore|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 Se il percorso completo non contiene un componente (ad esempio, un nome di file), `_splitpath_s` assegna una stringa vuota al buffer corrispondente.  
  
 In C++ l'uso di queste funzioni è semplificato dagli overload dei modelli. Gli overload possono dedurre la lunghezza del buffer automaticamente, eliminando la necessità di specificare un argomento di dimensione. Per altre informazioni, vedere [Overload di modelli sicuri](../../c-runtime-library/secure-template-overloads.md).  
  
 Le versioni di debug di queste funzioni riempiono innanzitutto il buffer con 0xFD. Per disabilitare questo comportamento, usare [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`_splitpath_s`|\<stdlib.h>|  
|`_wsplitpath_s`|\<stdlib.h> o \<wchar.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md) nell'introduzione.  
  
## <a name="example"></a>Esempio  
 See the example for [_makepath_s, _wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di file](../../c-runtime-library/file-handling.md)   
 [_splitpath, _wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)