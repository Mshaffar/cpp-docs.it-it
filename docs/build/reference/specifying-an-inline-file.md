---
title: Specifica di un file inline
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
ms.openlocfilehash: 7eb123ef3f2115df5c65d266630bded8cb54baae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318537"
---
# <a name="specifying-an-inline-file"></a>Specifica di un file inline

Specificare due parentesi angolari (<<) nel comando in cui *filename* deve essere visualizzato. Le parentesi acute non può essere un'espansione di macro.

## <a name="syntax"></a>Sintassi

```
<<[filename]
```

## <a name="remarks"></a>Note

Quando viene eseguito il comando, le parentesi acute vengono sostituite dalle *filename*, se specificato, o da un nome univoco generato NMAKE. Se specificato, *filename* deve seguire angolari senza spazi o tabulazioni. È consentito un percorso. Nessuna estensione è necessaria o si presuppone che. Se *filename* viene specificato, viene creato il file corrente o di directory specificato, sovrascrivendo quelli file con tale nome; in caso contrario, viene creato nella directory /TMP (o nella directory corrente, se la variabile di ambiente TMP non è definito). Se un precedente *filename* viene riutilizzato, NMAKE sostituisce il file precedente.

## <a name="see-also"></a>Vedere anche

[File inline in un makefile](inline-files-in-a-makefile.md)
