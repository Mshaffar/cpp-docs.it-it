---
title: _query_new_handler
ms.date: 11/04/2016
api_name:
- _query_new_handler
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _query_new_handler
- query_new_handler
helpviewer_keywords:
- query_new_handler function
- handler routines
- error handling
- _query_new_handler function
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
ms.openlocfilehash: 0cbd434ee0b75f78a2492bd6239bd89f584215ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949687"
---
# <a name="_query_new_handler"></a>_query_new_handler

Restituisce l'indirizzo della routine del nuovo gestore corrente.

## <a name="syntax"></a>Sintassi

```C
_PNH _query_new_handler(
   void
);
```

## <a name="return-value"></a>Valore restituito

Restituisce l'indirizzo della routine del nuovo gestore corrente impostata da **_set_new_handler**.

## <a name="remarks"></a>Note

La C++ funzione **_query_new_handler** restituisce l'indirizzo della funzione di gestione delle eccezioni corrente impostata dalla C++ funzione [_set_new_handler](set-new-handler.md) . **_set_new_handler** viene usato per specificare una funzione di gestione delle eccezioni che deve ottenere il controllo se l'operatore **New** non riesce ad allocare memoria. Per altre informazioni, vedere la discussione relativa agli [operatori new e delete](../../cpp/new-and-delete-operators.md) nelle informazioni di riferimento sul linguaggio C++.

## <a name="requirements"></a>Requisiti

|Routine|Intestazione obbligatoria|
|-------------|---------------------|
|**_query_new_handler**|\<new.h>|

Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Librerie

Tutte le versioni delle [librerie di runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vedere anche

[Allocazione di memoria](../../c-runtime-library/memory-allocation.md)<br/>
[free](free.md)<br/>
