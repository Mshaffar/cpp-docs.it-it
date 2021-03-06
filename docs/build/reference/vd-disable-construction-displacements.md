---
title: /vd (Disabilita spostamenti costruttori)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: db198dbdc7bd43ffd4de9bde39ee81a8b95a25ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316886"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Disabilita spostamenti costruttori)

## <a name="syntax"></a>Sintassi

```
/vdn
```

## <a name="arguments"></a>Argomenti

**0**<br/>
Elimina il membro di spostamento di vtordisp costruttore/distruttore. Scegliere questa opzione solo se si è certi che tutti i costruttori della classe e i distruttori chiamano virtuali virtualmente le funzioni.

**1**<br/>
Consente la creazione di membri di vtordisp nascosti costruttore/distruttore distanziato dello spostamento. Questa scelta è l'impostazione predefinita.

**2**<br/>
Consente di usare [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) su un oggetto in fase di costruzione. Ad esempio, un dynamic_cast da una classe base virtuale per una classe derivata.

**/ vd2** aggiunge un campo di vtordisp quando si dispone di una base virtuale per le funzioni virtuali. **/ vd1** dovrebbero essere sufficienti. I più comuni caso in cui **/vd2** è necessaria quando la funzione virtuale esclusivamente in base virtuale è un distruttore.

## <a name="remarks"></a>Note

Queste opzioni si applicano solo al codice C++ che utilizza basi virtuali.

Visual C++ implementa il supporto di C++ la costruzione dello spostamento in situazioni in cui viene utilizzata l'ereditarietà virtuale. Costruttori risolve il problema creato quando una funzione virtuale dichiarata in una base virtuale e sottoposto a override in una classe derivata, viene chiamato da un costruttore durante la costruzione di un'ulteriore classe derivata.

Il problema è che la funzione virtuale è possibile passare un'implementazione non corretta `this` puntatore come conseguenza di discrepanze tra gli spostamenti nelle virtuale basi di una classe e gli spostamenti nelle relative classi derivate. La soluzione fornisce una modifica allo spostamento di costruzione unico, definita campo di vtordisp, per ogni base virtuale di una classe.

Per impostazione predefinita, sono introdotta vtordisp (campi) ogni volta che il codice definisce i distruttori e i costruttori definiti dall'utente ed esegue inoltre l'override di funzioni virtuali di basi virtuali.

Queste opzioni influiscono interi file di origine. Uso [vtordisp](../../preprocessor/vtordisp.md) per eliminare e quindi riabilitare i campi vtordisp classe per classe.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Fare clic sulla cartella **C/C++** .

1. Fare clic sulla pagina delle proprietà **Riga di comando** .

1. Digitare l'opzione del compilatore nella casella **Opzioni aggiuntive** .

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vedere anche

[Opzioni del compilatore MSVC](compiler-options.md)<br/>
[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)
