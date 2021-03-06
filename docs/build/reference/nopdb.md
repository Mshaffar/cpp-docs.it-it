---
title: /NOPDB
description: L'opzione/NOPDB impedisce a DUMPBIN di caricare e cercare informazioni sui simboli nei file PDB.
ms.date: 12/04/2019
f1_keywords:
- /NOPDB
helpviewer_keywords:
- /NOPDB dumpbin option
- /NOPDB
ms.openlocfilehash: 7b0c01e59b52bcec6ddf09416dd6aac9999527a6
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856969"
---
# <a name="nopdb"></a>/NOPDB

Indica a DUMPBIN di non caricare e cercare le informazioni sui simboli nei file del database di programma (PDB).

## <a name="syntax"></a>Sintassi

> **/NOPDB**

## <a name="remarks"></a>Note

Per impostazione predefinita, DUMPBIN tenta di caricare i file PDB per i relativi file eseguibili di destinazione. DUMPBIN utilizza queste informazioni per trovare una corrispondenza tra gli indirizzi e i nomi dei simboli. Il processo può richiedere molto tempo se i file PDB sono di grandi dimensioni o devono essere caricati da un server remoto. L'opzione **/NOPDB** indica a DUMPBIN di ignorare questo passaggio. Vengono stampati solo gli indirizzi e le informazioni sui simboli disponibili nell'eseguibile.

### <a name="to-set-the-nopdb-linker-option-in-visual-studio"></a>Per impostare l'opzione del linker/NOPDB in Visual Studio

1. Aprire la finestra di dialogo **pagine delle proprietà** per il progetto. Per altre informazioni, vedere [Impostare il compilatore e le proprietà di compilazione](../working-with-project-properties.md).

1. Selezionare le **proprietà di configurazione** > **linker** > pagina delle proprietà **riga di comando** .

1. Nella casella **Opzioni aggiuntive** aggiungere l'opzione **/NOPDB** . Scegliere **OK** o **applica** per salvare le modifiche.

### <a name="to-set-this-linker-option-programmatically"></a>Per impostare l'opzione del linker a livello di codice

- Questa opzione non ha un equivalente a livello di codice.

## <a name="see-also"></a>Vedere anche

\ della [riga di comando DUMPBIN](dumpbin-command-line.md)
[Opzioni di DUMPBIN](dumpbin-options.md)\
[Riferimento a DUMPBIN](dumpbin-reference.md)
