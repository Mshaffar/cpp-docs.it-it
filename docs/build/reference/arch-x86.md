---
title: "/arch (x86) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
caps.latest.revision: 33
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 33
---
# /arch (x86)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Specifica l'architettura per la generazione del codice su piattaforme x86.  Vedere anche [\/arch \(x64\)](../../build/reference/arch-x64.md) e [\/arch \(ARM\)](../../build/reference/arch-arm.md).  
  
## Sintassi  
  
```  
/arch:[IA32|SSE|SSE2|AVX|AVX2]  
```  
  
## Argomenti  
 **\/arch:IA32**  
 Non specifica istruzioni avanzate e specifica x87 per i calcoli a virgola mobile.  
  
 **\/arch:SSE**  
 Abilita l'uso delle istruzioni SSE.  
  
 **\/arch:SSE2**  
 Abilita l'uso delle istruzioni SSE2.  Si tratta dell'istruzione predefinita per le piattaforme x86 se non vengono specificate opzioni **\/arch**.  
  
 **\/arch:AVX**  
 Abilita l'uso di istruzioni Intel Advanced Vector Extensions.  
  
 **\/arch:AVX2**  
 Abilita l'uso di istruzioni Intel Advanced Vector Extensions 2.  
  
## Note  
 Le istruzioni SSE ed SSE2 sono presenti in vari processori Intel e AMD.  Le istruzioni AVX sono presenti nei processori Sandy Bridge di Intel e nei processori Bulldozer di AMD.  Le istruzioni AVX2 sono supportate dai processori Haswalle e Broadwell di Intel e dai processori AMD basati su Excavator.  
  
 Le macro `_M_IX86_FP`, `__AVX__` e `__AVX2__` indicano quale opzione del compilatore **\/arch** è stata usata.  Per altre informazioni, vedere [Macro predefinite](../../preprocessor/predefined-macros.md).  L'opzione **\/arch:AVX2** e la macro `__AVX2__` sono state introdotte in Visual Studio 2013 Update 2, versione 12.0.34567.1.  
  
 L'utilità di ottimizzazione sceglie quando e come usare le istruzioni SSE ed SSE2 quando è specificato **\/arch**.  Usa le istruzioni SSE ed SSE2 per alcuni calcoli a virgola mobile scalari, quando stabilisce che l'esecuzione dei calcoli sarà più veloce usando i registri e le istruzioni SSE\/SSE2 anziché lo stack di registri a virgola mobile x87.  Di conseguenza, nel codice potrebbe essere in uso una combinazione di istruzioni x87 ed SSE\/SSE2 per i calcoli a virgola mobile.  Inoltre, con **\/arch:SSE2** è possibile usare le istruzioni SSE2 per alcune operazioni integer a 64 bit.  
  
 Oltre a usare le istruzioni SSE ed SSE2, il compilatore usa anche altre istruzioni presenti nelle revisioni del processore che supportano SSE ed SSE2.  Un esempio è costituito dall'istruzione CMOV che ha fatto la sua prima apparizione nella revisione Pentium Pro dei processori Intel.  
  
 Poiché il compilatore x86 genera codice che usa istruzioni SSE2 per impostazione predefinita, è necessario specificare **\/arch:IA32** per disabilitare la generazione di istruzioni SSE ed SSE2 per i processori x86.  
  
 **\/arch** interessa solo la generazione del codice per le funzioni native.  Quando si usa [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) per eseguire la compilazione, **\/arch** non determina alcun effetto sulla generazione del codice per le funzioni gestite.  
  
 **\/arch** e [\/QIfist](../../build/reference/qifist-suppress-ftol.md) non possono essere usati nello stesso compilando.  In particolare, se non si usa `_controlfp` per modificare la parola di controllo FP, il codice di avvio in fase di esecuzione imposta il campo di controllo della precisione della parola di controllo FPU dell'istruzione x87 su 53 bit.  Di conseguenza, ogni operazione a virgola mobile e precisione doppia in un'espressione usa un significando a 53 bit e un esponente a 15 bit.  Tuttavia, ogni operazione a precisione singola SSE usa un significando a 24 bit e un esponente a 8 bit, mentre le operazioni a precisione doppia SSE2 usano un significando a 53 bit e un esponente a 11 bit.  Per altre informazioni, vedere [\_control87, \_controlfp, \_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md).  Queste differenze sono possibili in un albero delle espressioni, ma non nei casi in cui è coinvolta un'assegnazione utente dopo ogni sottoespressione.  Si consideri quanto segue.  
  
```c  
  
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.  
```  
  
 Rispetto a:  
  
```c  
  
t = f1 * f2;   // Do f1 * f2, round to the type of t.  
r = t + d;     // This should produce the same overall result   
               // whether x87 stack is used or SSE/SSE2 is used.  
```  
  
### Per impostare questa opzione del compilatore per le istruzioni AVX, AVX2, IA32, SSE o SSE2 in Visual Studio  
  
1.  Aprire la finestra di dialogo **Pagine delle proprietà** del progetto.  Per altre informazioni, vedere [Procedura: aprire le pagine delle proprietà dei progetti](../../misc/how-to-open-project-property-pages.md).  
  
2.  Selezionare la cartella **Proprietà di configurazione**, **C\/C\+\+**.  
  
3.  Selezionare la pagina **Generazione codice**.  
  
4.  Modificare la proprietà **Abilita set di istruzioni avanzate**.  
  
### Per impostare l'opzione del compilatore a livello di codice  
  
-   Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## Vedere anche  
 [\/arch \(Architettura minima della CPU\)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opzioni del compilatore](../../build/reference/compiler-options.md)   
 [Impostazione delle opzioni del compilatore](../../build/reference/setting-compiler-options.md)