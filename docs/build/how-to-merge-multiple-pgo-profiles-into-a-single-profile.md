---
title: 'Procedura: unire più profili PGO in un unico profilo'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 451c0f30a271f5dce3974e172766da4a23340b93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188873"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Procedura: unire più profili PGO in un unico profilo

L'ottimizzazione PGO (PGO) è un ottimo strumento per la creazione di file binari ottimizzati basati su uno scenario profilato. Ma cosa accade se si dispone di un'applicazione che presenta diversi scenari importanti, ma distinti? Come si crea un singolo profilo che PGO può usare da diversi scenari? In Visual Studio, PGO Manager, [pgomgr. exe](pgomgr.md), esegue questo processo per l'utente.

La sintassi per l'Unione dei profili è la seguente:

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

dove `num` è un peso facoltativo da usare per i file PGC aggiunti da questo merge. I pesi vengono in genere utilizzati se sono presenti scenari più importanti di altri o se sono presenti scenari che devono essere eseguiti più volte.

> [!NOTE]
> PGO Manager non funziona con i dati di profilo non aggiornati. Per unire un file PGC in un file con estensione PGD, il file con estensione PGC deve essere generato da un eseguibile creato dalla stessa chiamata di collegamento che ha generato il file PGD.

## <a name="examples"></a>Esempi

In questo esempio, PGO Manager aggiunge pgcFile. pgc a pgdFile. pgd sei volte:

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

In questo esempio, PGO Manager aggiunge pgcFile1. PGC e pgcFile2. pgc a pgdFile. PGD, due volte per ogni file PGC:

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Se PGO Manager viene eseguito senza argomenti del file. PGC, Cerca nella directory locale tutti i file con estensione PGC con lo stesso nome di base del file. PGD seguito da un punto esclamativo (!) e quindi da uno o più caratteri arbitrari. Se, ad esempio, nella directory locale sono presenti file test. PGD, test! 1. PGC, test2. PGC e test! Hello. PGC e il comando seguente viene eseguito dalla directory locale, **pgomgr** unisce test! 1. PGC e test! Hello. PGC in test. pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Vedere anche

[Ottimizzazioni guidate da profilo (PGO)](profile-guided-optimizations.md)
