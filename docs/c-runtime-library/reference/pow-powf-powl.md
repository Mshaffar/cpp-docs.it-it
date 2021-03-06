---
title: pow, powf, powl
ms.date: 4/2/2020
api_name:
- powl
- pow
- powf
- _o_pow
- _o_powf
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: 38e79b547ad49c6f1c0f5a784d710838afdec388
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916802"
---
# <a name="pow-powf-powl"></a>pow, powf, powl

Calcola *x* elevato alla potenza di *y*.

## <a name="syntax"></a>Sintassi

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>Parametri

*x*<br/>
Base.

*y*<br/>
Esponente.

## <a name="return-value"></a>Valore restituito

Restituisce il valore di *x*<sup>*y*</sup>. In caso di overflow o di underflow non viene stampato alcun messaggio di errore.

|Valori di x e y|Valore restituito di pow|
|-----------------------|-------------------------|
|*x* ! = 0,0 e *y* = = 0,0|1|
|*x* = = 0,0 e *y* = = 0,0|1|
|*x* = = 0,0 e *y* < 0|INF|

## <a name="remarks"></a>Osservazioni

**POW** non riconosce i valori a virgola mobile integrali maggiori di 2<sup>64</sup> (ad esempio, 1.0 E100).

**POW** ha un'implementazione che usa Streaming SIMD Extensions 2 (SSE2). Per informazioni e le restrizioni sull'uso dell'implementazione SSE2, vedere [_set_SSE2_enable](set-sse2-enable.md).

Poiché C++ consente l'overload, è possibile chiamare uno dei diversi overload di **POW**. In un programma C, **POW** accetta sempre due valori **Double** e restituisce un valore **Double** .

L'overload `pow(int, int)` non è più disponibile. Se si usa questo overload, il compilatore può generare [C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md). Per evitare questo problema, eseguire il cast del primo parametro a **Double**, **float**o **Long** **Double**.

Per impostazione predefinita, lo stato globale di questa funzione ha come ambito l'applicazione. Per modificare questa situazione, vedere [stato globale in CRT](../global-state.md).

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria (C)|Intestazione obbligatoria (C++)|
|-|-|-|
|**POW**, **powf**, **POWL**|\<math.h>|\<math.h> o \<cmath>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Esempio

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>Vedere anche

[Supporto a virgola mobile](../../c-runtime-library/floating-point-support.md) <br/>
[exp, expf, expl](exp-expf.md) <br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md) <br/>
[sqrt, sqrtf, sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
