---
title: /Oi (Genera funzioni intrinseche)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
ms.openlocfilehash: f3afedade6f99129c21069e5117daa4ceb616cc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320344"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Genera funzioni intrinseche)

Sostituisce alcune chiamate di funzione con form intrinseci o speciali della funzione che consentono all'applicazione eseguite più velocemente.

## <a name="syntax"></a>Sintassi

```
/Oi[-]
```

## <a name="remarks"></a>Note

I programmi che usano funzioni intrinseche sono più veloci perché non hanno il sovraccarico delle chiamate di funzione, ma potrebbero essere più grandi a causa del codice aggiuntivo creato.

Visualizzare [intrinseco](../../preprocessor/intrinsic.md) per altre informazioni su quali funzioni hanno formati intrinseci.

**/Oi** è solo una richiesta al compilatore di sostituire alcune chiamate di funzione con le funzioni intrinseche; il compilatore può chiamare la funzione (e non sostituire la chiamata di funzione con una funzione intrinseca) se si ottengono prestazioni migliori.

**x86 Specific**

Le funzioni a virgola mobile intrinseche non esegue alcun controllo speciali su valori di input e quindi funzionano in intervalli di input limitati e hanno condizioni limite le routine di libreria con lo stesso nome e la gestione delle eccezioni diverse. Usando i formati intrinseci reali implica la perdita di gestione delle eccezioni IEEE e dei `_matherr` e `errno` funzionalità; quest'ultimo comporta la perdita della conformità ANSI. Tuttavia, intrinseci possono velocizzare notevolmente la virgola mobile cospicuo della virgola programmi e per molti programmi, i problemi di conformità sono di scarso valore pratico.

È possibile usare la [Za](za-ze-disable-language-extensions.md) opzione del compilatore per eseguire l'override della generazione delle opzioni a virgola mobile intrinseche true. In tal caso le funzioni vengono generate come routine della libreria che passano gli argomenti direttamente al chip a virgola mobile anziché inserirli nello stack del programma.

**FINE x86 specifico**

Utilizziamo inoltre [intrinseco](../../preprocessor/intrinsic.md) per creare le funzioni intrinseche, o [funzione (C/C++)](../../preprocessor/function-c-cpp.md) per forzare in modo esplicito una chiamata di funzione.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Fare clic sulla cartella **C/C++** .

1. Scegliere il **ottimizzazione** pagina delle proprietà.

1. Modificare il **Abilita funzioni intrinseche** proprietà.

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.

## <a name="see-also"></a>Vedere anche

[Opzioni /O (ottimizza codice)](o-options-optimize-code.md)<br/>
[Opzioni del compilatore MSVC](compiler-options.md)<br/>
[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)<br/>
[Intrinseci del compilatore](../../intrinsics/compiler-intrinsics.md)
