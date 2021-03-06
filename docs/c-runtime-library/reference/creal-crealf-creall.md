---
title: creal, crealf, creall
ms.date: 03/30/2018
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: 4dcdf60fee6d57b5561b72b477aa1a8bb31f35f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171216"
---
# <a name="creal-crealf-creall"></a>creal, crealf, creall

Ottiene la parte reale di un numero complesso.

## <a name="syntax"></a>Sintassi

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>Parametri

*z*<br/>
Numero complesso.

## <a name="return-value"></a>Valore restituito

Parte reale della *z*.

## <a name="remarks"></a>Osservazioni

Poiché C++ consente l'overload, è possibile chiamare gli overload di **CREAL** che accettano valori **_Fcomplex** o **_Lcomplex** e restituiscono valori **float** o **long double** . In un programma C, **CREAL** accetta sempre un valore di **_Dcomplex** e restituisce un valore **Double** .

## <a name="requirements"></a>Requisiti

|Routine|Intestazione C|Header C++|
|-------------|--------------|------------------|
|**CREAL**, **crealf**, **Creall**|\<complex.h>|\<ccomplex>|

I tipi **_Fcomplex**, **_Dcomplex**e **_Lcomplex** sono equivalenti specifici di Microsoft dei tipi C99 nativi non implementati **float _Complex**, **Double _Complex**e **long double _Complex**, rispettivamente. Per altre informazioni sulla compatibilità, vedere [Compatibility](../../c-runtime-library/compatibility.md) (Compatibilità).

## <a name="see-also"></a>Vedere anche

[Riferimento alfabetico alle funzioni](crt-alphabetical-function-reference.md)<br/>
[_Cbuild, _FCbuild, _LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
