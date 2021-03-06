---
title: Pragma include_alias
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218898"
---
# <a name="include_alias-pragma"></a>Pragma include_alias

Specifica che quando *alias_filename* viene trovato in una `#include` direttiva, il compilatore sostituisce *actual_filename* al suo posto.

## <a name="syntax"></a>Sintassi

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **,** "*actual_filename*" **)** \
> **#pragma include_alias (** \< *alias_filename*>  **,** *actual_filename*) \<> 

## <a name="remarks"></a>Note

La direttiva pragma **include_alias** consente di sostituire i file con nomi o percorsi diversi per i nomi di file inclusi nei file di origine. Alcuni file System, ad esempio, consentono nomi di file di intestazione più lunghi rispetto al limite di file system FAT 8,3. Il compilatore non può semplicemente troncare i nomi più lunghi a 8,3, perché i primi otto caratteri dei nomi file di intestazione più lunghi potrebbero non essere univoci. Ogni volta che il compilatore vede la stringa alias_filename `#include` in una direttiva, sostituisce invece il nome *actual_filename* . Quindi carica il file di intestazione *actual_filename* . Questo pragma deve essere visualizzato prima delle direttive `#include` corrispondenti. Ad esempio:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

L'alias da cercare deve corrispondere esattamente alla specifica. Il caso, l'ortografia e l'utilizzo delle virgolette doppie o delle parentesi angolari devono corrispondere. Il pragma **include_alias** esegue una corrispondenza di stringa semplice nei nomi dei file. Non viene eseguita alcuna convalida del nome file. Se si considerando, ad esempio, le seguenti direttive,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

non viene eseguita alcuna sostituzione di alias, perché le stringhe del file di intestazione non corrispondono esattamente. Inoltre, i nomi di file di intestazione usati come argomenti `/Yu` per `/Yc` le opzioni del compilatore e `hdrstop` o per il pragma non vengono sostituiti. Ad esempio, se il file di origine contiene la seguente direttiva,

```cpp
#include <AppleSystemHeaderStop.h>
```

l'opzione del compilatore corrispondente deve essere

> **/YcAppleSystemHeaderStop.h**

È possibile usare il pragma **include_alias** per eseguire il mapping di qualsiasi nome file di intestazione a un altro. Ad esempio:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Non combinare i nomi file racchiusi tra virgolette doppie con nomi file racchiusi tra parentesi angolari. Ad esempio, date le due `#pragma include_alias` direttive precedenti, il compilatore non esegue alcuna sostituzione sulle direttive seguenti: `#include`

```cpp
#include <api.h>
#include "stdio.h"
```

Inoltre, la seguente diretta genera un errore:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Il nome file indicato nei messaggi di errore o come valore della macro predefinita `__FILE__` è il nome del file al termine della sostituzione. Ad esempio, vedere l'output dopo le direttive seguenti:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

Errore in *VERYLONGFILENAME. H* genera il messaggio di errore seguente:

```Output
myfile.h(15) : error C2059 : syntax error
```

Si noti inoltre che la transitività non è supportata. Date le seguenti direttive,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

il compilatore cerca il file *due. h* anziché *tre. h*.

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
