---
title: Dipendenti dedotti
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 2382dec960ef93fc2f73987ad27b4670768a68cc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826949"
---
# <a name="inferred-dependents"></a>Dipendenti dedotti

Un dipendente dedotto viene derivato da una regola di inferenza e viene valutato prima dei dipendenti espliciti. Se un dipendente dedotto non è aggiornato rispetto alla relativa destinazione, viene richiamato il blocco di comandi per la dipendenza. Se un dipendente dedotto non esiste o non è aggiornato rispetto al proprio dipendenti, NMAKE Aggiorna innanzitutto il dipendente dedotto. Per altre informazioni sui dipendenti dedotti, vedere [regole di inferenza](inference-rules.md).

## <a name="see-also"></a>Vedere anche

[Dipendenti](dependents.md)