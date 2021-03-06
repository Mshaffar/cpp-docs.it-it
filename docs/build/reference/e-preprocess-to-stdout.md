---
title: /E (Pre-elabora in stdout)
ms.date: 11/04/2016
f1_keywords:
- /e
helpviewer_keywords:
- -E compiler option [C++]
- /E compiler option [C++]
- preprocessor output, copy to stdout
- preprocessor output
ms.assetid: ddbb1725-d950-4978-ab2f-30a5cd7b778c
ms.openlocfilehash: 710be7e1dfc4de89bc1eed3e23e4803c561da10c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273261"
---
# <a name="e-preprocess-to-stdout"></a>/E (Pre-elabora in stdout)

Pre-elabora i file di origine C e C++ e copia i file pre-elaborati per il dispositivo di output standard.

## <a name="syntax"></a>Sintassi

```
/E
```

## <a name="remarks"></a>Note

In questo processo, vengono eseguite tutte le direttive del preprocessore, espansioni della macro vengono eseguite e vengono rimossi i commenti. Per mantenere i commenti nell'output pre-elaborato, usare il [/C (mantenere i commenti durante la pre-elaborazione)](c-preserve-comments-during-preprocessing.md) anche l'opzione del compilatore.

**/E** aggiunge `#line` direttive nell'output a inizio e alla fine di ogni file incluso e attorno alle righe rimosse dalle direttive del preprocessore per la compilazione condizionale. Queste direttive rinumerano le righe del file pre-elaborato. Di conseguenza, gli errori generati durante le fasi successive dell'elaborazione di fare riferimento ai numeri di riga del file di origine originale anziché alle righe del file pre-elaborato.

Il **/E** opzione disattiva la compilazione. È necessario eseguire nuovamente il file pre-elaborato per la compilazione. **/E** elimina anche i file di output dal **/FA**, **/Fa**, e **/Fm** opzioni. Per altre informazioni, vedere [/FA, /Fa (File di listato)](fa-fa-listing-file.md) e [/Fm (specifica file MAP)](fm-name-mapfile.md).

Per sopprimere `#line` direttive, usare il [/EP (pre-elabora in stdout senza direttive #line)](ep-preprocess-to-stdout-without-hash-line-directives.md) opzione.

Per inviare l'output pre-elaborato in un file anziché al `stdout`, usare il [/P (pre-elabora in un File)](p-preprocess-to-a-file.md) opzione.

Per sopprimere `#line` direttive e invia l'output pre-elaborato in un file, usare **/P** e **/EP** tra loro.

Non è possibile usare le intestazioni precompilate con il **/E** opzione.

Si noti che quando si pre-elaborazione in un file separato, gli spazi non vengono creati dopo il token. Questo può comportare un programma non valido o avere effetti collaterali imprevisti. Il programma seguente viene compilato correttamente:

```
#define m(x) x
m(int)main( )
{
   return 0;
}
```

Tuttavia, se si compila con:

```
cl -E test.cpp > test2.cpp
```

`int main` in test2 in modo non corretto sarà `intmain`.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Per impostare l'opzione del compilatore nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Fare clic sulla cartella **C/C++** .

1. Fare clic sulla pagina delle proprietà **Riga di comando** .

1. Digitare l'opzione del compilatore nella **opzioni aggiuntive**casella.

### <a name="to-set-this-compiler-option-programmatically"></a>Per impostare l'opzione del compilatore a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.

## <a name="example"></a>Esempio

La seguente riga di comando preelabora `ADD.C`, conserva i commenti, aggiunge `#line` direttive e visualizza il risultato nel dispositivo di output standard:

```
CL /E /C ADD.C
```

## <a name="see-also"></a>Vedere anche

[Opzioni del compilatore MSVC](compiler-options.md)<br/>
[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)
