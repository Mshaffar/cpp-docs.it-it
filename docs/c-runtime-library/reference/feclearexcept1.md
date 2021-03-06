---
title: feclearexcept1
ms.date: 04/05/2018
api_name:
- feclearexcept
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- feclearexcept
- fenv/feclearexcept
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
ms.openlocfilehash: 9899d7068a289e7d5f71cb42a8373869d60c3070
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941264"
---
# <a name="feclearexcept"></a>feclearexcept

Prova a cancellare i flag di eccezione a virgola mobile specificati dall'argomento.

## <a name="syntax"></a>Sintassi

```C
int feclearexcept(
   int excepts
);
```

### <a name="parameters"></a>Parametri

*excepts*<br/>
Flag di stato delle eccezioni da cancellare.

## <a name="return-value"></a>Valore restituito

Restituisce zero se *excepts* è zero o se tutte le eccezioni specificate sono state cancellate correttamente. In caso contrario, viene restituito un valore diverso da zero.

## <a name="remarks"></a>Note

La funzione **feclearexcept** tenta di cancellare i flag di stato delle eccezioni a virgola mobile specificati da *excepts*. La funzione supporta queste macro di eccezioni, definite in fenv.h:

|Macro di eccezioni|Descrizione|
|---------------------|-----------------|
|FE_DIVBYZERO|Si è verificato un errore di singolarità o polo in un'operazione precedente a virgola mobile. È stato creato un valore di infinità.|
|FE_INEXACT|La funzione è stata forzata ad arrotondare il risultato archiviato di un'operazione precedente a virgola mobile.|
|FE_INVALID|Si è verificato un errore di dominio in un'operazione precedente a virgola mobile.|
|FE_OVERFLOW|Si è verificato un errore di intervallo. Un risultato dell'operazione precedente a virgola mobile era troppo grande per essere rappresentato.|
|FE_UNDERFLOW|Un risultato dell'operazione precedente a virgola mobile era troppo piccolo per essere rappresentato con la massima precisione. È stato creato un valore denormalizzato.|
|FE_ALL_EXCEPT|OR bit per bit di tutte le eccezioni a virgola mobile supportate.|

L'argomento *excepts* può essere zero o l'operatore OR bit per bit di una o più delle macro di eccezioni supportate. Il risultato di qualsiasi altro valore di argomento non è definito.

## <a name="requirements"></a>Requisiti

|Funzione|Intestazione C|Intestazione C++|
|--------------|--------------|------------------|
|**feclearexcept**|\<fenv.h>|\<cfenv>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vedere anche

[Riferimento alfabetico alle funzioni](crt-alphabetical-function-reference.md)<br/>
[fetestexcept](fetestexcept1.md)<br/>
