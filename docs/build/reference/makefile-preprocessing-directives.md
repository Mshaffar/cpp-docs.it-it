---
title: Direttive di pre-elaborazione di makefile
ms.date: 06/14/2018
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 0945d0e1c149b7e1ab31b0dbbd5003f8b15a1e4d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826780"
---
# <a name="makefile-preprocessing-directives"></a>Direttive di pre-elaborazione di makefile

Direttive di pre-elaborazione non sono tra maiuscole e minuscole. Il punto iniziale di punto esclamativo (!) devono essere visualizzati all'inizio della riga. Zero o più spazi o tabulazioni possono essere visualizzati dopo il punto esclamativo, per il rientro.

- **!CMDSWITCHES** {**+** &#124; **-**}*option* ...

   Trasforma ogni *opzione* elencati o disattivare. Spazi o tabulazioni devono precedere il + o - operatore None possono apparire tra l'operatore e il [opzione lettere](nmake-options.md). Lettere non sono tra maiuscole e minuscole e vengono specificate senza una barra (/). Per abilitare alcune opzioni e gli altri off, utilizzare le specifiche di separato di **! CMDSWITCHES**.

   Solo /D, / I, /N e /S può essere usati in un makefile. In Tools. ini, tutte le opzioni sono consentite tranne /F, /HELP, /NOLOGO, / X, e /?. Le modifiche specificate in un blocco di descrizione non diventano effettive finché il blocco successivo di descrizione. Aggiorna questa direttiva **MAKEFLAGS**; le modifiche vengono ereditate durante la ricorsione se **MAKEFLAGS** è specificato.

- **!ERROR**  *text*

   Consente di visualizzare *testo* errore U1050, quindi arresta NMAKE, anche se /K, / I, **. IGNORARE**, **! CMDSWITCHES**, o viene usato il modificatore di comandi trattino (-). Spazi o tabulazioni prima *testo* vengono ignorati.

- **!MESSAGE**  *text*

   Consente di visualizzare *testo* all'output standard. Spazi o tabulazioni prima *testo* vengono ignorati.

- **!INCLUDE** [ **\<** ] *filename* [ **>** ]

   Legge *filename* come un makefile, continua quindi con il file di progetto corrente. NMAKE cerca *nomefile* innanzitutto nella directory specificata o in atto, quindi in modo ricorsivo nelle directory dei padre makefile, quindi, se *filename* è racchiuso tra parentesi angolari (\<>), nelle directory specificate dal **Includi** (macro), che inizialmente è impostata la variabile di ambiente INCLUDE. Utile passare **. I SUFFISSI** le impostazioni, **. PREZIOSE**e delle regole di inferenza per makefile ricorsivi.

- **!IF** *constant_expression*

   Elaborazione di istruzioni racchiuse tra parentesi **! IF** e la successiva **! ELSE** o **! ENDIF** se *constant_expression* restituisce un valore diverso da zero.

- **!IFDEF**  *macroname*

   Elaborazione di istruzioni racchiuse tra parentesi **! IFDEF** e la successiva **! ELSE** o **! ENDIF** se *nomemacro* è definito. Macro null viene considerata definito.

- **! IFNDEF***nomemacro*

   Elaborazione di istruzioni racchiuse tra parentesi **! IFNDEF** e la successiva **! ELSE** o **! ENDIF** se *nomemacro* non è definito.

- **!ELSE** [**IF** *constant_expression* &#124; **IFDEF** *macroname* &#124; **IFNDEF** *macroname*]

   Elaborazione di istruzioni racchiuse tra parentesi **! ELSE** e la successiva **! ENDIF** se il prima **! IF**, **! IFDEF**, o **! IFNDEF** istruzione valutata a zero. Le parole chiave facoltative forniscono ulteriormente il controllo di pre-elaborazione.

- **!ELSEIF**

   Sinonimo di **! Se INVECE**.

- **!ELSEIFDEF**

   Sinonimo di **! IFDEF ELSE**.

- **!ELSEIFNDEF**

   Sinonimo di **! IFNDEF ELSE**.

- **!ENDIF**

   Contrassegna la fine di un **! IF**, **! IFDEF**, o **! IFNDEF** blocco. Qualsiasi testo che segue **! ENDIF** sulla stessa riga viene ignorata.

- **! UNDEF***nomemacro*

   Annullamenti *nomemacro*.

## <a name="see-also"></a>Vedere anche

- [Pre-elaborazione di makefile](makefile-preprocessing.md)