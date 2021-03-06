---
title: isnan, _isnan, _isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: a0cc60fb80f8d5b78ec2947a87fde82a536b413c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953757"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan, _isnan, _isnanf

Verifica se un valore a virgola mobile non è un numero (NaN, Not a Number).

## <a name="syntax"></a>Sintassi

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>Parametri

*x*<br/>
Valore a virgola mobile da verificare.

## <a name="return-value"></a>Valore restituito

In C, la macro **isNaN** e le funzioni **_isnan** e **isnanf** restituiscono un valore diverso da zero se l'argomento *x* è NaN; in caso contrario, restituiscono 0.

In C++la funzione di modello **isNaN** restituisce **true** se l'argomento *x* è NaN; in caso contrario, restituisce **false**.

## <a name="remarks"></a>Note

Poiché un valore NaN non è uguale a un altro valore NaN, è necessario usare una di queste funzioni o macro per rilevarne una. Un valore NaN viene generato quando il risultato di un'operazione a virgola mobile non può essere rappresentato nel formato a virgola mobile IEEE-754 per il tipo specificato. Per informazioni sulla rappresentazione di un valore NaN per l'output, vedere [printf](printf-printf-l-wprintf-wprintf-l.md).

Quando viene compilato C++come, la macro **isNaN** non è definita e viene invece definita una funzione di modello **isNaN** . Si comporta allo stesso modo della macro, ma restituisce un valore di tipo **bool** anziché un Integer.

Le funzioni **_isnan** e **isnanf** sono specifiche di Microsoft. La funzione **isnanf** è disponibile solo se compilata per x64.

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria (C)|Intestazione obbligatoria (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**, **_isnanf**|\<math.h>|\<math.h> o \<cmath>|
|**_isnan**|\<float.h>|\<float.h> o \<cfloat>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vedere anche

[Supporto delle funzioni a virgola mobile](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
