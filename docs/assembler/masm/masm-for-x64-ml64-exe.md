---
title: MASM per x64 (ml64.exe)
ms.date: 12/17/2019
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 5e324414a0d4d7e74bb28d54c1d858ef6fb9793c
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312742"
---
# <a name="masm-for-x64-ml64exe"></a>MASM per x64 (ml64.exe)

Visual Studio include versioni ospitate sia a 32 bit che a 64 bit di Microsoft assembler (MASM) per la destinazione di codice x64. Denominato ml64. exe, si tratta dell'assembler che accetta il linguaggio Assembler x64. Gli strumenti da riga di comando MASM vengono installati quando si sceglie C++ un carico di lavoro durante l'installazione di Visual Studio. Gli strumenti MASM non sono disponibili come download separato. Per istruzioni su come scaricare e installare una copia di Visual Studio, vedere [installare Visual Studio](/visualstudio/install/install-visual-studio). Se non si vuole installare l'IDE completo di Visual Studio, ma si vuole solo usare gli strumenti da riga di comando, scaricare gli [strumenti di compilazione per Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Per usare MASM per compilare il codice per le destinazioni x64 nella riga di comando, è necessario usare un prompt dei comandi per gli sviluppatori per le destinazioni x64, che imposta il percorso necessario e altre variabili di ambiente. Per informazioni su come avviare un prompt dei comandi per gli sviluppatori, vedere [compilareC++ C/codice nella riga di comando](../../build/building-on-the-command-line.md).

Per informazioni sulle opzioni della riga di comando ml64. exe, vedere informazioni di [riferimento sulla riga di comando ml e ml64](ml-and-ml64-command-line-reference.md).

L'assembler inline o l'uso della parola chiave ASM non è supportato per le destinazioni x64 o ARM. Per trasferire il codice x86 che usa l'assembler inline a x64 o ARM, è possibile convertire il codice C++in, usare oggetti intrinseci del compilatore o creare file di origine in linguaggio Assembler. Il compilatore C++ Microsoft supporta le funzioni intrinseche per consentire l'uso di istruzioni di funzione speciale, ad esempio con privilegi, analisi di bit/test, Interlocked e così via, nel modo più vicino possibile. Per informazioni sulle funzioni intrinseche disponibili, vedere [funzioni intrinseche del compilatore](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>Aggiungere un file in linguaggio assembler a un progetto di C++ Visual Studio

Il sistema di progetto di Visual Studio supporta i file in linguaggio Assembler compilati C++ usando MASM nei progetti. È possibile creare file di origine in linguaggio Assembler x64 e compilarli in file oggetto utilizzando MASM, che supporta completamente x64. È quindi possibile collegare questi file oggetto al codice C++ compilato per le destinazioni x64. Questo è un modo per ovviare alla mancanza di un assembler inline x64.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>Per aggiungere un file in linguaggio assembler a un progetto di Visual C++ Studio esistente

1. Selezionare il progetto in **Esplora soluzioni**. Sulla barra dei menu scegliere **progetto**, **personalizzazioni compilazione**.

1. Nella finestra di dialogo **file di personalizzazione della compilazione C++ visuale** Selezionare la casella di controllo accanto a **MASM (. targets,. props)** . Scegliere **OK** per salvare la selezione e chiudere la finestra di dialogo.

1. Sulla barra dei menu scegliere **progetto**, **Aggiungi nuovo elemento**.

1. Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare  **C++ file (. cpp)** nel riquadro centrale. Nel controllo modifica **nome** immettere un nuovo nome file con estensione **ASM** anziché cpp. Scegliere **Aggiungi** per aggiungere il file al progetto e chiudere la finestra di dialogo.

Creare il codice in linguaggio assembler nel file con estensione ASM aggiunto. Quando si compila la soluzione, l'assembler MASM viene richiamato per assemblare il file ASM in un file oggetto che viene quindi collegato al progetto. Per semplificare l'accesso ai simboli, dichiarare le funzioni dell'assembler come `extern "C"` C++ nel codice sorgente, anziché usare le C++ convenzioni di decorazione dei nomi nei file di origine del linguaggio Assembler.

## <a name="ml64-specific-directives"></a>Direttive specifiche di ml64

È possibile usare le direttive specifiche di ml64 seguenti nel codice sorgente del linguaggio Assembler destinato a x64:

- [.ALLOCSTACK](dot-allocstack.md)

- [.ENDPROLOG](dot-endprolog.md)

- [.PUSHFRAME](dot-pushframe.md)

- [.PUSHREG](dot-pushreg.md)

- [.SAVEREG](dot-savereg.md)

- [.SAVEXMM128](dot-savexmm128.md)

- [.SETFRAME](dot-setframe.md)

Inoltre, la direttiva [proc](proc.md) è stata aggiornata per l'utilizzo con ml64. exe.

## <a name="32-bit-address-mode-address-size-override"></a>Modalità Indirizzo 32 bit (override delle dimensioni degli indirizzi)

MASM genera l'override della dimensione dell'indirizzo 0x67 se un operando di memoria include registri a 32 bit. Gli esempi seguenti, ad esempio, determinano la creazione dell'override delle dimensioni dell'indirizzo:

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM presuppone che se lo spostamento a 32 bit viene visualizzato da solo come operando di memoria, è previsto l'indirizzamento a 64 bit. Attualmente non è disponibile alcun supporto per l'indirizzamento a 32 bit con tali operandi.

Infine, combinando le dimensioni del registro all'interno di un operando di memoria, come illustrato nel codice seguente, viene generato un errore.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Vedere anche

[Riferimento a Microsoft Macro Assembler](microsoft-macro-assembler-reference.md)
