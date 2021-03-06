---
title: /USEPROFILE (dati di utilizzo PGO con LTCG)
ms.date: 03/14/2018
f1_keywords:
- USEPROFILE
ms.openlocfilehash: 7bc0033ae5ef512cbd2e2063c5cb9bd9b061c180
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317133"
---
# <a name="useprofile-run-pgo-in-thread-safe-mode"></a>/USEPROFILE (PGO eseguito in modalità provvisoria thread)

Questa opzione del linker assieme [/LTCG (generazione di codice in fase di collegamento](ltcg-link-time-code-generation.md) indica al linker per compilare usando dati di training di ottimizzazione PGO (PGO).

## <a name="syntax"></a>Sintassi

> **/USEPROFILE**[**:**{**AGGRESSIVE**|**PGD=**_filename_}]

### <a name="arguments"></a>Argomenti

**AGGRESSIVA**<br/>
Questo argomento facoltativo consente di specificare che le ottimizzazioni aggressiva velocità devono essere utilizzate durante la generazione del codice ottimizzato.

**PGD**=*nomefile*<br/>
Specifica un nome del file di base per il file PGD. Per impostazione predefinita, il linker Usa il nome base file eseguibile con estensione pgd.

## <a name="remarks"></a>Note

Il **/USEPROFILE** viene usata in combinazione con l'opzione del linker **/LTCG** per generare o aggiornare una build ottimizzata basata sui dati di training PGO. È l'equivalente di deprecate **/LTCG: PGUPDATE** e **/LTCG: PGOPTIMIZE** opzioni.

L'opzione facoltativa **stile di Guida AGGRESSIVO** argomento disabilita l'euristica correlati alla dimensione per tentare di ottimizzare la velocità. Questo può comportare ottimizzazioni che sostanzialmente aumentare le dimensioni del file eseguibile e non possono aumentare la velocità risulta. È consigliabile profilare e confrontare i risultati dell'uso e non usa **stile di Guida AGGRESSIVO**. Questo argomento deve essere specificato in modo esplicito. non è abilitato per impostazione predefinita.

Il **PGD** argomento specifica un nome facoltativo per il file pgd i dati di training da usare, come in [/GENPROFILE o /fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md). È l'equivalente di deprecate **/PGD** passare. Per impostazione predefinita, o se nessun *filename* viene specificato, un file PDG che ha lo stesso nome di base viene usato il file eseguibile.

Il **/USEPROFILE** l'opzione del linker è stata introdotta in Visual Studio 2015.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Per impostare questa opzione del linker nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Selezionare il **le proprietà di configurazione** > **Linker** > **ottimizzazione** pagina delle proprietà.

1. Nel **Link Time Code Generation** proprietà, scegliere **generazione codice in fase di collegamento Usa (/ LTCG)**.

1. Selezionare il **le proprietà di configurazione** > **Linker** > **della riga di comando** pagina delle proprietà.

1. Immettere il **/USEPROFILE** opzione e gli argomenti facoltativi nel **opzioni aggiuntive** casella. Scegliere **OK** per salvare le modifiche.

### <a name="to-set-this-linker-option-programmatically"></a>Per impostare l'opzione del linker a livello di codice

- Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vedere anche

[/ GENPROFILE e /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/LTCG](ltcg-link-time-code-generation.md)<br/>
[Ottimizzazioni PGO](../profile-guided-optimizations.md)<br/>
[Variabili d'ambiente per le ottimizzazioni GPO](../environment-variables-for-profile-guided-optimizations.md)<br/>
