---
title: _get_errno
ms.date: 4/2/2020
api_name:
- _get_errno
- _o__get_errno
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_errno
helpviewer_keywords:
- get_errno function
- errno global variable
- _get_errno function
ms.assetid: b3fd5ebc-f41b-4314-a2f4-2f2d79d6e740
ms.openlocfilehash: f1678628685c74519077fb68ca9c810aebe30fdd
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919349"
---
# <a name="_get_errno"></a>_get_errno

Ottiene il valore corrente della variabile globale errno.

## <a name="syntax"></a>Sintassi

```C
errno_t _get_errno(
   int * pValue
);
```

### <a name="parameters"></a>Parametri

*pValue*<br/>
Puntatore a un Integer da riempire con il valore corrente della variabile **errno** .

## <a name="return-value"></a>Valore restituito

Restituisce zero se ha esito positivo; un codice di errore se ha esito negativo. Se *pValue* è **null**, viene richiamato il gestore di parametri non validi, come descritto in [convalida dei parametri](../../c-runtime-library/parameter-validation.md). Se l'esecuzione può continuare, questa funzione imposta **errno** su **EINVAL** e restituisce **EINVAL**.

## <a name="remarks"></a>Osservazioni

I valori possibili di **errno** sono definiti in errno. h. Vedere anche [Costanti errno](../../c-runtime-library/errno-constants.md).

Per impostazione predefinita, lo stato globale di questa funzione ha come ambito l'applicazione. Per modificare questa situazione, vedere [stato globale in CRT](../global-state.md).

## <a name="example"></a>Esempio

```C
// crt_get_errno.c
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <share.h>
#include <errno.h>

int main()
{
   errno_t err;
   int pfh;
   _sopen_s( &pfh, "nonexistent.file", _O_WRONLY, _SH_DENYNO, _S_IWRITE );
   _get_errno( &err );
   printf( "errno = %d\n", err );
   printf( "fyi, ENOENT = %d\n", ENOENT );
}
```

```Output
errno = 2
fyi, ENOENT = 2
```

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|Intestazione facoltativa|
|-------------|---------------------|---------------------|
|**_get_errno**|\<stdlib.h>|\<errno.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vedere anche

[_set_errno](set-errno.md)<br/>
[errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
