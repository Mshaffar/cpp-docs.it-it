---
title: _aligned_free_dbg
ms.date: 11/04/2016
api_name:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: 18c1a23d666070afaf1eff687c7d33b0240f0ac3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171281"
---
# <a name="_aligned_free_dbg"></a>_aligned_free_dbg

Libera un blocco di memoria che è stato allocato con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) (solo versione di debug).

## <a name="syntax"></a>Sintassi

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>Parametri

*memblock*<br/>
Puntatore al blocco di memoria restituito alla funzione [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md) .

## <a name="remarks"></a>Osservazioni

La funzione **_aligned_free_dbg** è una versione di debug della funzione [_aligned_free](aligned-free.md) . Quando [_DEBUG](../../c-runtime-library/debug.md) non è definito, ogni chiamata a **_aligned_free_dbg** viene ridotta a una chiamata a `_aligned_free`. Sia `_aligned_free` che **_aligned_free_dbg** liberare un blocco di memoria nell'heap di base, ma **_aligned_free_dbg** supporta una funzionalità di debug: la possibilità di tenere i blocchi liberati nell'elenco collegato dell'heap per simulare condizioni di memoria insufficiente.

**_aligned_free_dbg** esegue un controllo di validità su tutti i file e i percorsi dei blocchi specificati prima di eseguire l'operazione gratuita. Non è previsto che l'applicazione fornisca queste informazioni. Quando un blocco di memoria viene liberato, il gestore dell'heap di debug controlla automaticamente l'integrità dei buffer a ogni lato della porzione utente e genera un rapporto errori se si sono verificate sovrascritture. Se viene impostato il campo _CRTDBG_DELAY_FREE_MEM_DF bit del flag [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) , il blocco liberato viene riempito con il valore 0xDD, viene assegnato il tipo di blocco _FREE_BLOCK e mantenuto nell'elenco collegato dell'heap dei blocchi di memoria.

Se si verifica un errore nel liberare la memoria, `errno` viene impostato con informazioni dal sistema operativo sulla natura dell'errore. Per altre informazioni, vedere [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (errno, _doserrno, _sys_errlist e _sys_nerr).

Per informazioni sulle modalità di allocazione, inizializzazione e gestione dei blocchi di memoria nella versione di debug dell'heap di base, vedere [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details) (Informazioni dettagliate sull'heap di debug CRT). Per informazioni sui tipi di blocchi di allocazione e su come vengono usati, vedere [Tipi di blocchi sull'heap di debug](/visualstudio/debugger/crt-debug-heap-details). Per informazioni sulle differenze tra chiamare una funzione standard dell'heap e la sua versione di debug nella build di debug di un'applicazione, vedere [Versioni di debug di funzioni di allocazione heap](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibility](../../c-runtime-library/compatibility.md) (Compatibilità).

## <a name="see-also"></a>Vedere anche

[Routine di debug](../../c-runtime-library/debug-routines.md)
