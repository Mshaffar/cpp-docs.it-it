---
title: 'Server: Implementazione di un Server'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 953d157f4bbad0b460947740a2622074dfc90f4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308017"
---
# <a name="servers-implementing-a-server"></a>Server: Implementazione di un Server

Questo articolo illustra il codice che crea la creazione guidata applicazione MFC per un'applicazione server di modifica visiva. Se non si usa la creazione guidata applicazione, in questo articolo elenca le aree in cui è necessario scrivere codice per implementare un'applicazione server.

Se si utilizza la creazione guidata applicazione per creare una nuova applicazione server, fornisce una quantità significativa di codice specifico del server per l'utente. Se si aggiunge visual funzionalità server di modifica a un'applicazione esistente, è necessario duplicare il codice che verrebbe sono fornite per la creazione guidata applicazione prima di aggiungere il resto del codice del server necessari.

Il codice di server che fornisce la creazione guidata applicazioni rientra nelle diverse categorie:

- Definizione delle risorse di server:

  - La risorsa di menu usata quando il server viene modificato un elemento incorporato in una finestra.

  - Le risorse di menu e barra degli strumenti usate quando il server è attivo sul posto.

  Per altre informazioni su queste risorse, vedere [menu e risorse: Aggiunte di server](../mfc/menus-and-resources-server-additions.md).

- La definizione di una classe dell'elemento derivato da `COleServerItem`. Per ulteriori informazioni su elementi del server, vedere [server: Gli elementi del server](../mfc/servers-server-items.md).

- Modifica della classe di base della classe documento da `COleServerDoc`. Per altre informazioni, vedere [server: Implementazione di documenti Server](../mfc/servers-implementing-server-documents.md).

- Definizione di una classe di finestre cornice derivato da `COleIPFrameWnd`. Per altre informazioni, vedere [server: Implementazione di Windows sul posto Frame](../mfc/servers-implementing-in-place-frame-windows.md).

- Creazione di una voce per l'applicazione server in database di registrazione Windows e registrando la nuova istanza del server con il sistema OLE. Per informazioni su questo argomento, vedere [registrazione](../mfc/registration.md).

- L'inizializzazione e l'avvio dell'applicazione server. Per informazioni su questo argomento, vedere [registrazione](../mfc/registration.md).

Per altre informazioni, vedere [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), e [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) nel *Class Library Reference*.

## <a name="see-also"></a>Vedere anche

[Server](../mfc/servers.md)<br/>
[Contenitori](../mfc/containers.md)<br/>
[Menu e risorse (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Registrazione](../mfc/registration.md)
