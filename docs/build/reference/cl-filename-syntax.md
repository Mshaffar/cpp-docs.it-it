---
title: Sintassi nome file di CL
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: 1135e5c682b79fec5de808b61c93d370f05a3aa9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440233"
---
# <a name="cl-filename-syntax"></a>Sintassi nome file di CL

CL accetta file con nomi che seguono le convenzioni di denominazione FAT, HPFS o NTFS. Tutti i nomi file possono includere un percorso completo o parziale. Un percorso completo include un nome di unità e uno o più nomi di directory. CL accetta i nomi file separati da barre rovesciate (\\) o barre (/). I nomi file che contengono spazi devono essere racchiusi tra virgolette doppie. Un percorso parziale omette il nome dell'unità, che CL considera essere l'unità corrente. Se non si specifica un percorso, il file verrà considerato come presente nella directory attuale.

L'estensione del nome file determina il modo in cui i file vengono elaborati. I file C e C++, che hanno l'estensione c, cxx o cpp, vengono compilati. Altri file, inclusi i file obj, di libreria (lib) e di definizione moduli (def) vengono passati al linker senza essere elaborati.

## <a name="see-also"></a>Vedere anche

[Sintassi della riga di comando del compilatore MSVC](compiler-command-line-syntax.md)
