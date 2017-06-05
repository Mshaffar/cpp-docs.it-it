---
title: fesetenv | Documenti Microsoft
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
- fesetenv
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
- fesetenv
- fenv/fesetenv
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 6
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
ms.openlocfilehash: 96453fb182aa3c14bec8a296899cfcd15d39222c
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="fesetenv"></a>fesetenv
Imposta l'ambiente a virgola mobile corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
int fesetenv(  
   const fenv_t *penv  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `penv`  
 Puntatore a un oggetto `fenv_t` che contiene un ambiente a virgola mobile impostato da una chiamata a [fegetenv](fegetenv1.md) o a [feholdexcept](feholdexcept2.md). È anche possibile specificare l'ambiente a virgola mobile di avvio predefinito tramite la macro FE_DFL_ENV.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce 0 se l'ambiente è stato impostato correttamente. In caso contrario, viene restituito un valore diverso da zero.  
  
## <a name="remarks"></a>Note  
 La funzione `fesetenv` imposta l'ambiente a virgola mobile corrente dal valore archiviato nell'oggetto `fenv_t` a cui punta `penv`. L'ambiente a virgola mobile è il set di flag dello stato e le modalità di controllo che influiscono sui calcoli a virgola mobile. Ciò include la modalità di arrotondamento e i flag di stato delle eccezioni a virgola mobile.  Se `penv` non è FE_DFL_ENV oppure non punta a un oggetto `fenv_t` valido, il successivo comportamento non è definito.  
  
 Una chiamata a questa funzione imposta i flag di stato delle eccezioni dell'oggetto `penv`, ma non genera queste eccezioni.  
  
 Per usare questa funzione, è necessario disattivare le ottimizzazioni a virgola mobile che potrebbero impedire l'accesso tramite la direttiva `#pragma fenv_access(on)` prima della chiamata. Per altre informazioni, vedere [fenv_access](../../preprocessor/fenv-access.md).  
  
## <a name="requirements"></a>Requisiti  
  
|Funzione|Intestazione C|Intestazione C++|  
|--------------|--------------|------------------|  
|`fesetenv`|\<fenv.h>|\<cfenv>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibility](../../c-runtime-library/compatibility.md) (Compatibilità).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alfabetico alle funzioni](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetenv](../../c-runtime-library/reference/fegetenv1.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)