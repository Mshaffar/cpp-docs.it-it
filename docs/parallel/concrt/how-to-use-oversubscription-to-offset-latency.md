---
title: "Procedura: Usare l'oversubscription per compensare la latenza"
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
ms.openlocfilehash: 02c72e7b7f0e3ec9727504d62341d945dcd0d957
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141946"
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Procedura: Usare l'oversubscription per compensare la latenza

Oversubscription può migliorare l'efficienza complessiva di alcune applicazioni che contengono attività con un elevato livello di latenza. In questo argomento viene illustrato come utilizzare l'oversubscription per compensare la latenza causata dalla lettura di dati da una connessione di rete.

## <a name="example"></a>Esempio

Questo esempio usa la [libreria di agenti asincroni](../../parallel/concrt/asynchronous-agents-library.md) per scaricare i file dai server http. La classe `http_reader` deriva da [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md) e utilizza il passaggio del messaggio per leggere in modo asincrono i nomi URL da scaricare.

La classe `http_reader` usa la classe [Concurrency:: task_group](reference/task-group-class.md) per leggere simultaneamente ogni file. Ogni attività chiama il metodo [Concurrency:: context:: Oversubscribe](reference/context-class.md#oversubscribe) con il parametro `_BeginOversubscription` impostato su **true** per abilitare l'oversubscription nel contesto corrente. Ogni attività USA quindi le classi Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) e [CHttpFile](../../mfc/reference/chttpfile-class.md) per scaricare il file. Infine, ogni attività chiama `Context::Oversubscribe` con il parametro `_BeginOversubscription` impostato su **false** per disabilitare l'oversubscription.

Quando oversubscription è abilitato, il runtime crea un thread aggiuntivo in cui eseguire le attività. Ognuno di questi thread può anche sovrascrivere il contesto corrente e quindi creare thread aggiuntivi. La classe `http_reader` utilizza un oggetto [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) per limitare il numero di thread utilizzati dall'applicazione. L'agente Inizializza il buffer con un numero fisso di valori di token. Per ogni operazione di download, l'agente legge un valore del token dal buffer prima che l'operazione venga avviata, quindi scrive nuovamente il valore nel buffer al termine dell'operazione. Quando il buffer è vuoto, l'agente attende che una delle operazioni di download riscriva un valore nel buffer.

Nell'esempio seguente viene limitato il numero di attività simultanee a due volte il numero di thread hardware disponibili. Questo valore è un buon punto di partenza da usare quando si sperimenta l'oversubscription. È possibile utilizzare un valore che soddisfi un particolare ambiente di elaborazione oppure modificare dinamicamente questo valore per rispondere al carico di lavoro effettivo.

[!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]

Questo esempio produce l'output seguente in un computer che dispone di quattro processori:

```Output
Downloading http://www.adatum.com/...
Downloading http://www.adventure-works.com/...
Downloading http://www.alpineskihouse.com/...
Downloading http://www.cpandl.com/...
Downloading http://www.cohovineyard.com/...
Downloading http://www.cohowinery.com/...
Downloading http://www.cohovineyardandwinery.com/...
Downloading http://www.contoso.com/...
Downloading http://www.consolidatedmessenger.com/...
Downloading http://www.fabrikam.com/...
Downloading http://www.fourthcoffee.com/...
Downloading http://www.graphicdesigninstitute.com/...
Downloading http://www.humongousinsurance.com/...
Downloading http://www.litwareinc.com/...
Downloading http://www.lucernepublishing.com/...
Downloading http://www.margiestravel.com/...
Downloading http://www.northwindtraders.com/...
Downloading http://www.proseware.com/...
Downloading http://www.fineartschool.net...
Downloading http://www.tailspintoys.com/...
Downloaded 1801040 bytes in 3276 ms.
```

L'esempio può essere eseguito più velocemente quando oversubscription è abilitato perché vengono eseguite attività aggiuntive mentre altre attività attendono il completamento di un'operazione latente.

## <a name="compiling-the-code"></a>Compilazione del codice

Copiare il codice di esempio e incollarlo in un progetto di Visual Studio oppure incollarlo in un file denominato `download-oversubscription.cpp`, quindi eseguire uno dei comandi seguenti in una finestra del **prompt dei comandi di Visual Studio** .

```cmd
cl.exe /EHsc /MD /D "_AFXDLL" download-oversubscription.cpp
cl.exe /EHsc /MT download-oversubscription.cpp
```

## <a name="robust-programming"></a>Programmazione efficiente

Disabilitare sempre l'oversubscription dopo che non è più necessario. Si consideri una funzione che non gestisce un'eccezione generata da un'altra funzione. Se non si disabilita l'oversubscription prima della restituzione della funzione, eventuali operazioni parallele aggiuntive eseguiranno anche l'oversubscription del contesto corrente.

È possibile usare il modello di *inizializzazione della risorsa* (RAII) per limitare l'oversubscription a un ambito specifico. Nel modello RAII, viene allocata una struttura di dati nello stack. La struttura dei dati Inizializza o acquisisce una risorsa quando viene creata ed Elimina o rilascia la risorsa quando la struttura dei dati viene distrutta. Il modello RAII garantisce che il distruttore venga chiamato prima che l'ambito di inclusione venga chiuso. La risorsa viene pertanto gestita correttamente quando viene generata un'eccezione o quando una funzione contiene più istruzioni `return`.

Nell'esempio seguente viene definita una struttura denominata `scoped_blocking_signal`. Il costruttore della struttura `scoped_blocking_signal` Abilita l'oversubscription e il distruttore Disabilita l'oversubscription.

[!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]

Nell'esempio seguente viene modificato il corpo del metodo `download` per utilizzare RAII per garantire che l'oversubscription venga disabilitato prima che la funzione restituisca. Questa tecnica garantisce che il metodo `download` sia indipendente dalle eccezioni.

[!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]

## <a name="see-also"></a>Vedere anche

[Contesti](../../parallel/concrt/contexts.md)<br/>
[Metodo Context:: Oversubscribe](reference/context-class.md#oversubscribe)
