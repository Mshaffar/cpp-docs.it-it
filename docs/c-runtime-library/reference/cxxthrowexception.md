---
title: _CxxThrowException
ms.date: 11/04/2016
api_name:
- _CxxThrowException
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CxxThrowException
- _CxxThrowException
helpviewer_keywords:
- _CxxThrowException function
- CxxThrowException function
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
ms.openlocfilehash: a5b614d25502ddd5a58aedcf2ec843b2b1ab9d47
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942031"
---
# <a name="_cxxthrowexception"></a>_CxxThrowException

Compila il record di eccezione e chiama l'ambiente di runtime per iniziare a elaborare l'eccezione.

## <a name="syntax"></a>Sintassi

```C
extern "C" void __stdcall _CxxThrowException(
   void* pExceptionObject
   _ThrowInfo* pThrowInfo
);
```

### <a name="parameters"></a>Parametri

*pExceptionObject*<br/>
L'oggetto che ha generato l'eccezione.

*pThrowInfo*<br/>
Le informazioni necessarie per elaborare l'eccezione.

## <a name="remarks"></a>Note

Questo metodo è incluso in un file del compilatore che il compilatore usa per elaborare le eccezioni. Non chiamare il metodo direttamente dal codice.

## <a name="requirements"></a>Requisiti

**Origine** Throw. cpp

## <a name="see-also"></a>Vedere anche

[Riferimento alfabetico alle funzioni](crt-alphabetical-function-reference.md)<br/>
