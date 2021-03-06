---
title: Server
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: 7b1eb0df439bcfde3aa295f23a90291e865df3a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307835"
---
# <a name="servers"></a>Server

Un'applicazione server (o un componente applicazione) Crea OLE elementi (o i componenti) per l'utilizzo da applicazioni contenitore. Un'applicazione server di modifica visiva supporta anche la modifica visiva o attivazione sul posto. Un altro tipo di server OLE è un' [server di automazione](../mfc/automation-servers.md). Alcune applicazioni server supportano solo la creazione di elementi incorporati; altri supportano la creazione di elementi collegati e incorporati. Alcuni supportano il collegamento solo, sebbene sia raro. Tutte le applicazioni server devono supportare l'attivazione per le applicazioni contenitore quando l'utente desidera modificare un elemento. Un'applicazione può essere sia un contenitore e un server. In altre parole, possono incorporare i dati all'interno dei documenti e creare i dati che possono essere incorporati come elementi in documenti di altre applicazioni.

Un server ridotto è un tipo speciale di applicazione server che può essere avviata unicamente da un contenitore. Draw Microsoft e Microsoft Graph sono esempi di server ridotti. Un server ridotto i documenti non vengono archiviati come file su disco. Al contrario, ai documenti da legge e scrive gli elementi nei documenti che appartengono a contenitori. Di conseguenza, un server ridotto supporta solo l'incorporamento, non il collegamento.

Un server completo può essere eseguito come un'applicazione autonoma o avviato da un'applicazione contenitore. Un server completo possa archiviare i documenti come file su disco. Può supportare l'incorporamento, solo l'incorporamento e di collegamento o solo il collegamento. L'utente di un'applicazione contenitore può creare un elemento incorporato scegliendo il comando Taglia o copia nel server e il comando Incolla nel contenitore. Scegliendo il comando copia nel server e il comando Incolla collegamento nel contenitore viene creato un elemento collegato. In alternativa, l'utente può creare un elemento incorporato o collegato utilizzando la finestra di dialogo Inserisci oggetto.

La tabella seguente riepiloga le caratteristiche dei diversi tipi di server:

### <a name="server-characteristics"></a>Caratteristiche del server

|Tipo di server|Supporta più istanze|Elementi per ogni documento|Documenti per ogni istanza|
|--------------------|---------------------------------|------------------------|----------------------------|
|Miniserver|Yes|1|1|
|Completo del server SDI|Yes|1 (se il collegamento è supportato, 1 o più)|1|
|Server completo MDI|No (non necessaria)|1 (se il collegamento è supportato, 1 o più)|0 o maggiore di|

Un'applicazione server deve supportare più contenitori contemporaneamente, nel caso in cui verrà usato più di un contenitore per modificare un elemento incorporato o collegato. Se il server è un'applicazione SDI (o un server ridotto con un'interfaccia della finestra di dialogo), più istanze del server devono essere in grado di eseguire contemporaneamente. In questo modo un'istanza separata dell'applicazione per gestire ogni richiesta di contenitore.

Se il server è un'applicazione MDI, è possibile creare una nuova finestra figlio MDI ogni volta che un contenitore deve modificare un elemento. In questo modo, una singola istanza dell'applicazione può supportare più contenitori.

L'applicazione server deve indicare DLL del sistema OL cosa fare se un'istanza del server è già in esecuzione quando un altro contenitore richiede i servizi: se devono avviare una nuova istanza del server o di indirizzare le richieste di tutti i contenitori a un'istanza del Server.

Per altre informazioni sui server, vedere:

- [Server: implementazione di un server](../mfc/servers-implementing-a-server.md)

- [Server: implementazione di documenti server](../mfc/servers-implementing-server-documents.md)

- [Server: implementazione di finestre cornice sul posto](../mfc/servers-implementing-in-place-frame-windows.md)

- [Server: elementi server](../mfc/servers-server-items.md)

- [Server: problemi dell'interfaccia utente](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>Vedere anche

[OLE](../mfc/ole-in-mfc.md)<br/>
[Contenitori](../mfc/containers.md)<br/>
[Contenitori: funzionalità avanzate](../mfc/containers-advanced-features.md)<br/>
[Menu e risorse (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Registrazione](../mfc/registration.md)<br/>
[Server di automazione](../mfc/automation-servers.md)
