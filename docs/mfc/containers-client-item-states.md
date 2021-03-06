---
title: 'Contenitori: Stati elementi client'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 1453ba3f96e49cefc9014a93ebcfbcfe5c6bc905
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152852"
---
# <a name="containers-client-item-states"></a>Contenitori: Stati elementi client

Questo articolo illustra i diversi stati di che un elemento client passa attraverso il ciclo di vita.

Un elemento client passa attraverso diversi stati così come viene creato, attivata, modificato e salvato. Ogni volta che cambia lo stato dell'elemento, il framework chiama [COleClientItem:: OnChange](../mfc/reference/coleclientitem-class.md#onchange) con il **OLE_CHANGED_STATE** notifica. Il secondo parametro è un valore compreso il `COleClientItem::ItemState` enumerazione. Può essere uno dei seguenti:

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

Nello stato vuoto, un elemento client non è ancora completamente un elemento. È stata allocata memoria adatto, ma non è ancora stato inizializzato con i dati dell'elemento OLE. Questo è lo stato di un elemento client viene in dopo che è stato creato tramite una chiamata a **nuovo** ma non è ancora stata eseguita il secondo passaggio della creazione del tipico in due passaggi.

Nel secondo passaggio, eseguito tramite una chiamata a `COleClientItem::CreateFromFile` o un altro `CreateFrom` *xxxx* (funzione), l'elemento viene completamente creato. I dati OLE (da un file o un'altra origine, ad esempio negli Appunti) sono stati associati il `COleClientItem`-oggetto derivato. A questo punto l'elemento è nello stato caricato.

Quando un elemento è stato aperto nella finestra del server anziché sul posto nel documento del contenitore, è nello stato aperto (o completamente aperto). In questo stato, un tratteggio incrociato in genere viene creato tramite la rappresentazione dell'elemento nella finestra del contenitore per indicare che l'elemento è attivo in un' posizione.

Quando un elemento è stato attivato sul posto, ha esito positivo, in genere solo brevemente, tramite lo stato attivo. Quindi passa lo stato attivo dell'interfaccia utente, in cui il server è unito relativo menu, barre degli strumenti e altri componenti dell'interfaccia utente con quelli del contenitore. La presenza di questi componenti dell'interfaccia utente consente di distinguere lo stato attivo dell'interfaccia utente dallo stato attivo. In caso contrario, lo stato attivo è simile allo stato attivo dell'interfaccia utente. Se il server supporta l'annullamento, il server è necessario conservare informazioni sullo stato di annullamento di un elemento OLE finché non raggiunge lo stato caricato o aperto.

## <a name="see-also"></a>Vedere anche

[Contenitori](../mfc/containers.md)<br/>
[Attivazione](../mfc/activation-cpp.md)<br/>
[Contenitori: Notifiche elementi client](../mfc/containers-client-item-notifications.md)<br/>
[Tracker](../mfc/trackers.md)<br/>
[Classe CRectTracker](../mfc/reference/crecttracker-class.md)
