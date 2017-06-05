---
title: _RTC_SetErrorType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
dev_langs:
- C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 78f056e65523a39477bf138e6bd1664e0945a899
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="rtcseterrortype"></a>_RTC_SetErrorType
Associa un errore che viene rilevato dai controlli degli errori di run-time a un tipo. Il gestore di errori elabora le modalità di output degli errori del tipo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      int _RTC_SetErrorType(  
   _RTC_ErrorNumber errnum,  
   int ErrType   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 *errnum*  
 Numero compreso tra zero e uno minore del valore restituito da [_RTC_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md).  
  
 *ErrType*  
 Valore da assegnare a questo *errnum*. Ad esempio, si può usare **_CRT_ERROR**. Se si usa `_CrtDbgReport` come gestore di errori, *ErrType* può rappresentare solo uno dei simboli definiti in [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md). Se si ha un proprio gestore di errori ([_RTC_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md)), è possibile avere un numero di *ErrType*pari al numero di *errnum*.  
  
 Un valore *ErrType* di _RTC_ERRTYPE_IGNORE ha un significato speciale per `_CrtSetReportMode`. L'errore viene ignorato.  
  
## <a name="return-value"></a>Valore restituito  
 Valore precedente per il tipo di errore `type`.  
  
## <a name="remarks"></a>Note  
 Per impostazione predefinita, tutti gli errori vengono impostati su *ErrType* = 1, che corrisponde a **_CRT_ERROR**. Per altre informazioni sui tipi di errore predefiniti come **_CRT_ERROR**, vedere [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
 Prima di chiamare questa funzione, è necessario chiamare una delle funzioni di inizializzazione dei controlli degli errori di runtime. Vedere [Uso dei controlli runtime senza la libreria di runtime del linguaggio C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`_RTC_SetErrorType`|\<rtcapi.h>|  
  
 Per altre informazioni, vedere [Compatibilità](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Librerie  
 Tutte le versioni delle [librerie di runtime C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vedere anche  
 [_RTC_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [Controllo degli errori di runtime](../../c-runtime-library/run-time-error-checking.md)