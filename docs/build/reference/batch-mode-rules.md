---
title: Regole in modalità batch
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328405"
---
# <a name="batch-mode-rules"></a>Regole in modalità batch

```
{frompath}.fromext{topath}.toext::
   commands
```

Le regole di inferenza in modalità batch forniscono una sola chiamata della regola di inferenza quando i comandi N passano attraverso questa regola di inferenza. Senza regole di inferenza in modalità batch, sarebbe necessario N comandi da richiamare. N è il numero di dipendenti che attivano la regola di inferenza.

I makefile che contengono regole di inferenza in modalità batch devono utilizzare NMAKE versione 1.62 o successiva. Per verificare la versione di NMAKE, eseguire la macro _NMAKE_VER disponibile con NMAKE versione 1.62 o successiva. Questa macro restituisce una stringa che rappresenta la versione del prodotto Visual C.

L'unica differenza sintattica rispetto alla regola di inferenza standard è che la regola di inferenza in modalità batch viene terminata con due punti doppi (::).

> [!NOTE]
> Lo strumento richiamato deve essere in grado di gestire più file. La regola di inferenza `$<` in modalità batch deve essere utilizzata come macro per accedere ai file dipendenti.

Le regole di inferenza in modalità batch possono velocizzare il processo di compilazione. È più veloce fornire i file al compilatore in batch, perché il driver del compilatore viene richiamato una sola volta. Ad esempio, le prestazioni del compilatore C e C, ovvero C, funzionano meglio quando si gestisce un set di file, perché può rimanere residente in memoria durante il processo.

Nell'esempio seguente viene illustrato come utilizzare le regole di inferenza in modalità batch:The following example shows how to use batch-mode inference rules:

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE produce il seguente output senza regole di inferenza in modalità batch:

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

NMAKE produce il seguente risultato con le regole di inferenza in modalità batch:

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>Vedere anche

[Regole di inferenza](inference-rules.md)
