---
title: _execl, _wexecl
ms.date: 11/04/2016
api_name:
- _execl
- _wexecl
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execl
- _wexecl
- wexecl
helpviewer_keywords:
- _execl function
- wexecl function
- _wexecl function
- execl function
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
ms.openlocfilehash: 714ef80c4909e92100c4fa869b7544239f8edeb7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941944"
---
# <a name="_execl-_wexecl"></a>_execl, _wexecl

Carica ed esegue nuovi processi figlio.

> [!IMPORTANT]
> Non è possibile usare questa API nelle applicazioni eseguite in Windows Runtime. Per altre informazioni, vedere [Funzioni CRT non supportate nelle app della piattaforma UWP (Universal Windows Platform)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintassi

```C
intptr_t _execl(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexecl(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parametri

*cmdname*<br/>
Percorso del file da eseguire.

*arg0*, ... *argn*<br/>
Elenco di puntatori ai parametri.

## <a name="return-value"></a>Valore restituito

Se l'operazione riesce, le funzioni non ritornano al processo chiamante. Il valore restituito-1 indica un errore, nel qual caso è impostata la variabile globale **errno** .

|Valore errno|Descrizione|
|-----------------|-----------------|
|**E2BIG**|Lo spazio necessario per gli argomenti e le impostazioni di ambiente supera 32 KB.|
|**EACCES**|Il file specificato dispone di una violazione di blocco o di condivisione.|
|**EINVAL**|Parametro non valido (uno o più parametri sono puntatori Null o stringhe vuote).|
|**EMFILE**|Troppi file aperti (il file specificato deve essere aperto per determinare se sia eseguibile).|
|**ENOENT**|Il file o il percorso non è stato trovato.|
|**ENOEXEC**|Il file specificato non è eseguibile o il formato del file eseguibile non è valido.|
|**ENOMEM**|Memoria insufficiente per eseguire il nuovo processo; la memoria disponibile è stata danneggiata; o esiste un blocco non valido che indica che il processo chiamante non è stato allocato correttamente.|

## <a name="remarks"></a>Note

Ognuna di queste funzioni carica ed esegue un nuovo processo, passando ogni argomento della riga di comando come parametro separato. Il primo argomento è il comando o il nome del file eseguibile e il secondo argomento deve essere uguale al primo. Diventa `argv[0]` nel processo eseguito. Il terzo argomento è il primo argomento, `argv[1]`, del processo in esecuzione.

Le funzioni **_execl** convalidano i relativi parametri. Se *CmdName* o *arg0* è un puntatore null o una stringa vuota, queste funzioni richiamano il gestore di parametri non validi, come descritto in [convalida dei parametri](../../c-runtime-library/parameter-validation.md) se l'esecuzione può continuare, queste funzioni impostano **errno** su  **EINVAL** e return-1. Non viene eseguito alcun nuovo processo.

## <a name="requirements"></a>Requisiti

|Funzione|Intestazione obbligatoria|Intestazione facoltativa|
|--------------|---------------------|---------------------|
|**_execl**|\<process.h>|\<errno.h>|
|**_wexecl**|\<process.h> o \<wchar.h>|\<errno.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Esempio

Vedere l'esempio in [Funzioni _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Vedere anche

[Controllo di processi e ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[Funzioni _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[Funzioni _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
