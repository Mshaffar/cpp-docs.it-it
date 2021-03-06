---
title: Comandi di un makefile
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: fcb8737070931cf95d7bfb3971a84e22c7ad70a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294395"
---
# <a name="commands-in-a-makefile"></a>Comandi di un makefile

Una regola di blocco o inferenza descrizione specifica un blocco di comandi da eseguire se la dipendenza non è aggiornata. NMAKE ogni comando viene visualizzato prima dell'esecuzione, a meno che non /S, **. SILENT**, **! CMDSWITCHES**, o \@ viene usato. Se un blocco di descrizione non è seguito da un blocco di comandi, viene cercata una regola di inferenza dei tipi corrispondente.

Un blocco di comandi contiene uno o più comandi, ognuno nella propria riga. Nessuna riga vuota può essere presenti tra la dipendenza o la regola e il blocco di comandi. Tuttavia, può essere visualizzata una riga che contiene solo spazi o tabulazioni. Questa riga viene interpretata come un comando null e verrà generato alcun errore. Righe vuote sono consentite tra le righe di comando.

Una riga di comando inizia con uno o più spazi o tabulazioni. Una barra rovesciata (\) seguita da un carattere di nuova riga viene interpretata come spazio nel comando. usare una barra rovesciata alla fine di una riga per continuare il comando nella riga successiva. VIENE interpretato letteralmente la barra rovesciata se qualsiasi altro carattere, inclusi spazi o tabulazioni, segue la barra rovesciata.

Un comando preceduto da un punto e virgola (;) possono essere visualizzati in una regola di riga o inferenza dipendenza, se un blocco di comandi seguente:

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>Scegliere l'argomento su cui visualizzare maggiori informazioni

[Modificatori di comandi](command-modifiers.md)

[Sintassi relativa ai nomi file](filename-parts-syntax.md)

[File inline in un makefile](inline-files-in-a-makefile.md)

## <a name="see-also"></a>Vedere anche

[Riferimenti a NMAKE](nmake-reference.md)
