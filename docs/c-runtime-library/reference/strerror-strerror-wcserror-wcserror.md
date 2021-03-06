---
title: strerror, _strerror, _wcserror, __wcserror
description: Descrive le funzioni della libreria di runtime Microsoft C (CRT) strerror, _strerror, _wcserror e __wcserror.
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
ms.openlocfilehash: 30885974b9c9fbf0fdca0e52808fb8bd1dfbaffe
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920038"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Ottiene una stringa del messaggio di errore di sistema (**strerror**, **_wcserror**) o formatta una stringa del messaggio di errore fornita dall'utente (**_strerror**, **__wcserror**). Sono disponibili versioni più sicure di queste funzioni. Vedere [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Sintassi

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>Parametri

*errnum*\
Numero di errore.

*strErrMsg*\
Messaggio fornito dall'utente.

## <a name="return-value"></a>Valore restituito

Tutte queste funzioni restituiscono un puntatore a una stringa di messaggio di errore, in un buffer di archiviazione locale di thread di proprietà del runtime. Le chiamate successive sullo stesso thread possono sovrascrivere questa stringa.

## <a name="remarks"></a>Osservazioni

La funzione **strerror** esegue il mapping di *errnum* a una stringa di messaggio di errore e restituisce un puntatore alla stringa. Le funzioni **strerror** e **_strerror** non stampano effettivamente il messaggio. Per stampare, chiamare una funzione di output, ad esempio [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Se *strErrMsg* viene passato come **null**, **_strerror** restituisce un puntatore a una stringa. Contiene il messaggio di errore di sistema per l'ultima chiamata di libreria che ha generato un errore. La stringa del messaggio di errore termina con il carattere di nuova riga ("\n"). Quando *strErrMsg* non è **null**, la stringa contiene, nell'ordine: la stringa *strErrMsg* , i due punti, uno spazio, il messaggio di errore di sistema e un carattere di nuova riga. Il messaggio stringa può avere una lunghezza massima di 94 caratteri, in caratteri narrow (**_strerror**) o wide (**__wcserror**).

Il numero di errore effettivo per **_strerror** viene archiviato nella variabile [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Per produrre risultati accurati, chiamare **_strerror** immediatamente dopo la restituzione di un errore da una routine della libreria. In caso contrario, le chiamate successive alle routine della libreria possono sovrascrivere il valore **errno** .

**_wcserror** e **__wcserror** sono rispettivamente versioni a caratteri wide di **strerror** e **_strerror**.

**_strerror**, **_wcserror**e **__wcserror** sono specifici di Microsoft e non fanno parte della libreria C standard. Non è consigliabile usarli in cui si vuole usare il codice portatile. Per la compatibilità con il linguaggio C standard, usare invece **strerror** .

Per ottenere le stringhe di errore, è consigliabile usare **strerror** o **_wcserror** anziché le macro deprecate [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) e [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) e le funzioni interne deprecate **__sys_errlist** e **__sys_nerr**.

Per impostazione predefinita, lo stato globale di questa funzione ha come ambito l'applicazione. Per modificare questa situazione, vedere [stato globale in CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapping di routine di testo generico

|Routine TCHAR.H|_UNICODE e _MBCS non definiti|_MBCS definito|_UNICODE definito|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Esempio

Vedere l'esempio relativo a [perror](perror-wperror.md).

## <a name="see-also"></a>Vedere anche

[Manipolazione di stringhe](../../c-runtime-library/string-manipulation-crt.md)\
[clearerr](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
