---
title: Informazioni di riferimento sullo schema Tasks.vs.json (C++)
ms.date: 02/11/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: d0f62f6cddf3701da391880532bd2f554cc19130
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826449"
---
# <a name="tasksvsjson-c"></a>Tasks.vs.json (C++)

È possibile aggiungere un file `tasks.vs.json` a un progetto Apri cartella per definire un'attività arbitraria e quindi richiamarla dal menu di scelta rapida di **Esplora soluzioni**. I progetti CMake in genere non usano questo file perché tutti i comandi di compilazione sono specificati in `CMakeLists.txt`. Per i sistemi di compilazione diversi da CMake, questo file consente di specificare i comandi di compilazione e richiamare gli script di compilazione. Per informazioni generali sull'uso di tasks.vs.json, vedere [Personalizzare le attività di compilazione e debug per lo sviluppo con "Apri cartella"](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).
