---
title: _aligned_free
ms.date: 4/2/2020
api_name:
- _aligned_free
- _o__aligned_free
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: d296600da4db2b97479de95cfc1f8c41d0e50708
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915946"
---
# <a name="_aligned_free"></a>_aligned_free

Libera un blocco di memoria che è stato allocato con [_aligned_malloc](aligned-malloc.md) o [_aligned_offset_malloc](aligned-offset-malloc.md).

## <a name="syntax"></a>Sintassi

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>Parametri

*memblock*<br/>
Puntatore al blocco di memoria che è stato restituito alla funzione `_aligned_malloc` o `_aligned_offset_malloc`.

## <a name="remarks"></a>Osservazioni

**_aligned_free** è contrassegnato `__declspec(noalias)`, pertanto non è garantito che la funzione modifichi le variabili globali. Per altre informazioni, vedere [noalias](../../cpp/noalias.md).

Questa funzione non convalida il parametro, a differenza di altre funzioni CRT _aligned. Se *memblock* è un puntatore null, questa funzione non esegue semplicemente alcuna azione. Non modifica `errno` e non richiama il gestore di parametri non validi. Se si verifica un errore nella funzione a causa del mancato utilizzo precedente di funzioni _aligned per allocare il blocco di memoria oppure si verifica un problema di allineamento della memoria a causa di alcune calamità impreviste, la funzione genera un report di debug dalle [Macro _RPT, _RPTF, _RPTW, _RPTFW](rpt-rptf-rptw-rptfw-macros.md).

Per impostazione predefinita, lo stato globale di questa funzione ha come ambito l'applicazione. Per modificare questa situazione, vedere [stato globale in CRT](../global-state.md).

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>Esempio

Per altre informazioni, vedere [_aligned_malloc](aligned-malloc.md).

## <a name="see-also"></a>Vedere anche

[Allineamento dati](../../c-runtime-library/data-alignment.md)
