---
title: Esclusione del meccanismo di serializzazione | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b0beb14c2ddb159616f7cbb34b83b68e84ef0a1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="bypassing-the-serialization-mechanism"></a>Esclusione del meccanismo di serializzazione
Come si è visto, il framework fornisce una modalità predefinita per leggere e scrivere i dati da e verso i file. La serializzazione tramite un oggetto archivio soddisfi le esigenze di numerose applicazioni. Un'applicazione legge un file completamente in memoria, consente all'utente di aggiornare il file e quindi scrive la versione aggiornata sul disco.  
  
 Tuttavia, alcune applicazioni di operare sui dati in modo molto diverso, e per le applicazioni della serializzazione tramite un archivio non è adatta. Sono esempi di applicazioni di database, i programmi che modificano solo parti di file di grandi dimensioni, programmi che scrivono i file di solo testo e i programmi che condividono i file di dati.  
  
 In questi casi, è possibile eseguire l'override di [Serialize](../mfc/reference/cobject-class.md#serialize) funzione in modo diverso per la mediazione azioni del file tramite un [CFile](../mfc/reference/cfile-class.md) oggetto anziché da un [CArchive](../mfc/reference/carchive-class.md) oggetto.  
  
 È possibile utilizzare il **aprire**, **lettura**, **scrivere**, **Chiudi**, e `Seek` funzioni membro della classe `CFile` per aprire un file , spostare il puntatore del file (ricerca) a un momento specifico nel file di lettura di un record (un numero specificato di byte) a questo punto, consentono l'aggiornamento dell'utente del record, quindi cercare nuovamente nello stesso punto e scrivere il record aggiornato per il file. Il file verrà aperto il framework per l'utente ed è possibile utilizzare il `GetFile` funzione membro di classe `CArchive` per ottenere un puntatore al `CFile` oggetto. Per l'utilizzo di più complesso e flessibile, è possibile eseguire l'override di [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) e [OnSaveDocument](../mfc/reference/cdocument-class.md#onsavedocument) funzioni membro della classe `CWinApp`. Per ulteriori informazioni, vedere la classe [CFile](../mfc/reference/cfile-class.md) nel *riferimenti alla libreria MFC*.  
  
 In questo scenario, il `Serialize` override non esegue alcuna operazione, a meno che non, ad esempio, si desidera per la lettura e scrittura di un'intestazione di file per mantenere aggiornato alla chiusura del documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di documenti](../mfc/using-documents.md)
