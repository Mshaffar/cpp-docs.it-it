---
title: /PROFILE (Profiler strumenti di prestazioni)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: cf07154c6b681e2ad30a85a62a0db996c3f3d911
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078316"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profiler strumenti di prestazioni)

Produce un file di output che può essere usato con il profiler di Strumenti per le prestazioni.

## <a name="syntax"></a>Sintassi

```
/PROFILE
```

## <a name="remarks"></a>Osservazioni

/PROFILE implica le seguenti opzioni del linker:

- [/OPT: REF](opt-optimizations.md)

- /OPT: NOICF

- [/INCREMENTAL: NO](incremental-link-incrementally.md)

- [/FIXED: NO](fixed-fixed-base-address.md)

/PROFILE fa in modo che il linker generi una sezione di rilocazione nell'immagine del programma.  Una sezione di rilocazione consente al profiler di trasformare l'immagine del programma per ottenere i dati del profilo.

**/Profile** è disponibile solo nelle versioni Enterprise (Team Development).  Per altre informazioni su PREfast, vedere [analisi del codice per CC++ /Overview](/cpp/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Per impostare questa opzione del linker nell'ambiente di sviluppo di Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [Impostare le proprietà del compilatore e di compilazione C++ in Visual Studio](../working-with-project-properties.md).

1. Espandere il nodo **Proprietà di configurazione**.

1. Espandere il nodo **Linker**.

1. Selezionare la pagina delle proprietà **Avanzate**.

1. Modificare la proprietà del **profilo** .

### <a name="to-set-this-linker-option-programmatically"></a>Per impostare l'opzione del linker a livello di codice

1. Vedere <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

### <a name="to-set-this-linker-option-within-visual-studio-cmake-project"></a>Per impostare questa opzione del linker nel progetto CMake di Visual Studio

Il progetto **CMake** non dispone di una **pagina delle proprietà**. è possibile impostare le opzioni del linker modifica CMakeLists. txt.

1. Aprire CMakeLists. txt nella directory radice del progetto.

1. Aggiungere il codice seguente. Per informazioni dettagliate, vedere [riferimenti a CMake](https://cmake.org/cmake/help/v3.0/command/set_target_properties.html)

1. Ricompilare la soluzione.

```
SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/PROFILE")
```

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sul linker MSVC](linking.md)<br/>
[Opzioni del linker MSVC](linker-options.md)
