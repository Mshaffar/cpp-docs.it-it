---
title: "Procedure consigliate nella libreria PPL (Parallel Patterns Library) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Libreria PPL, procedure consigliate per evitare"
  - "procedure consigliate per evitare, Parallel Patterns Library"
  - "procedure consigliate, Parallel Patterns Library"
  - "Libreria PPL, procedure consigliate"
ms.assetid: e43e0304-4d54-4bd8-a3b3-b8673559a9d7
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedure consigliate nella libreria PPL (Parallel Patterns Library)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

In questo documento viene descritto come ottimizzare l'uso della libreria PPL (Parallel Patterns Library). In tale libreria sono disponibili contenitori, oggetti e algoritmi di uso generale che consentono di eseguire un parallelismo accurato.  
  
 Per ulteriori informazioni sulla libreria PPL, vedere [libreria PPL (Parallel Patterns Library)](../../parallel/concrt/parallel-patterns-library-ppl.md).  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> Nelle sezioni  
 Questo documento contiene le seguenti sezioni:  
  
- [Non parallelizzare corpi di ciclo di dimensioni ridotte](#small-loops)  
  
- [Esprimere il parallelismo al livello più alto](#highest)  
  
- [Utilizzare parallel_invoke per risolvere i problemi di Divide et impera](#divide-and-conquer)  
  
- [Utilizzare l'annullamento o eccezioni per interrompere un ciclo Parallel](#breaking-loops)  
  
- [Comprendere come annullamento e la gestione delle eccezioni influiscono sui eliminazione degli oggetti](#object-destruction)  
  
- [Non si bloccano più volte in un ciclo Parallel](#repeated-blocking)  
  
- [Non eseguire operazioni di blocco quando si annulla un lavoro parallelo](#blocking)  
  
- [Non scrivere ai dati condivisi in un ciclo Parallel](#shared-writes)  
  
- [Quando possibile, evitare di condividere False](#false-sharing)  
  
- [Assicurarsi che le variabili siano valide per tutta la durata di un'attività](#lifetime)  
  
##  <a name="a-namesmall-loopsa-do-not-parallelize-small-loop-bodies"></a><a name="small-loops"></a> Non parallelizzare corpi di ciclo di dimensioni ridotte  
 La parallelizzazione di corpi di ciclo di dimensioni relativamente ridotte può determinare un sovraccarico della pianificazione associata che annulla i vantaggi derivanti dall'elaborazione in parallelo. Si consideri l'esempio seguente, in cui ogni coppia di elementi viene aggiunta in due matrici.  
  
 [!code-cpp[concrt-small-loops#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_1.cpp)]  
  
 Il volume del carico di lavoro per ogni iterazione del ciclo parallelo è troppo piccolo per poter trarre vantaggio dal sovraccarico dell'elaborazione in parallelo. È possibile migliorare le prestazioni di questo ciclo eseguendo un maggior volume di lavoro nel corpo del ciclo oppure eseguendo il ciclo in modalità seriale.  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-namehighesta-express-parallelism-at-the-highest-possible-level"></a><a name="highest"></a> Esprimere il parallelismo al livello più alto  
 Quando il codice viene parallelizzato solo a un livello basso, è possibile introdurre un costrutto fork-join che non viene ridimensionato con l'aumento del numero di processori. Oggetto *divisione / unione* costrutto è un costrutto in cui un'attività di suddivisione del lavoro più piccoli sottoattività parallele e attende il completamento. Ciascuna sottoattività può a sua volta essere suddivisa in modo ricorsivo in ulteriori sottoattività.  
  
 Sebbene il modello fork-join possa risultare utile per risolvere vari problemi, in alcune situazioni il sovraccarico della sincronizzazione può diminuire la scalabilità. Si consideri, ad esempio, il codice seriale seguente che elabora i dati di immagine.  
  
 [!code-cpp[concrt-image-processing-filter#20](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_2.cpp)]  
  
 Poiché ogni iterazione del ciclo è indipendente, è possibile parallelizzare gran parte del lavoro, come illustrato nell'esempio seguente. Questo esempio viene utilizzato il [Concurrency:: parallel_for](../Topic/parallel_for%20Function.md) algoritmo per parallelizzare il ciclo esterno.  
  
 [!code-cpp[concrt-image-processing-filter#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_3.cpp)]  
  
 Nell'esempio seguente viene illustrato un costrutto fork-join mediante la chiamata alla funzione `ProcessImage` in un ciclo. Ogni chiamata a `ProcessImage` non comporta alcuna risposta fino al completamento di ciascuna sottoattività.  
  
 [!code-cpp[concrt-image-processing-filter#21](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_4.cpp)]  
  
 Se ogni iterazione del ciclo parallelo non esegue quasi alcun lavoro oppure il lavoro eseguito dal ciclo parallelo non è bilanciato, ovvero alcune iterazioni del ciclo richiedono più tempo di altre, il sovraccarico di pianificazione richiesto per eseguire con frequenza le operazioni di fork e join può annullare il vantaggio dell'esecuzione parallela. Questo sovraccarico aumenta con l'aumentare del numero di processori.  
  
 Per ridurre la quantità di sovraccarico di pianificazione in questo esempio, è possibile parallelizzare i cicli esterni prima di quelli interni oppure usare un altro costrutto parallelo come pipelining. Nell'esempio seguente viene modificato il `ProcessImages` funzione utilizzare la [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) algoritmo per parallelizzare il ciclo esterno.  
  
 [!code-cpp[concrt-image-processing-filter#22](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_5.cpp)]  
  
 Per un esempio simile che utilizza una pipeline per eseguire l'elaborazione di immagini in parallelo, vedere [procedura dettagliata: creazione di una rete di elaborazione delle immagini](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-namedivide-and-conquera-use-parallelinvoke-to-solve-divide-and-conquer-problems"></a><a name="divide-and-conquer"></a> Utilizzare parallel_invoke per risolvere i problemi di Divide et impera  
 Oggetto *divide et impera* problema è una forma del costrutto fork-join che utilizza la ricorsione per suddividere un'attività in sottoattività. Oltre al [Concurrency:: task_group](../Topic/task_group%20Class.md) e [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) classi, è inoltre possibile utilizzare il [Concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md) algoritmo per risolvere i problemi divide et impera. L'algoritmo `parallel_invoke` ha una sintassi più concisa rispetto agli oggetti gruppo di attività ed è utile quando è presente un numero fisso di attività parallele.  
  
 Nell'esempio seguente viene illustrato l'uso dell'algoritmo `parallel_invoke` per implementare l'algoritmo di ordinamento bitonico.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#12](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_6.cpp)]  
  
 Per ridurre il sovraccarico, l'algoritmo `parallel_invoke` esegue l'ultima delle serie di attività nel contesto di chiamata.  
  
 Per la versione completa di questo esempio, vedere [procedura: utilizzare parallel_invoke per scrivere una Routine di ordinamento parallelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md). Per ulteriori informazioni sui `parallel_invoke` algoritmo, vedere [algoritmi paralleli](../../parallel/concrt/parallel-algorithms.md).  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-namebreaking-loopsa-use-cancellation-or-exception-handling-to-break-from-a-parallel-loop"></a><a name="breaking-loops"></a> Utilizzare l'annullamento o eccezioni per interrompere un ciclo Parallel  
 La libreria PPL fornisce due modi per annullare il lavoro parallelo che viene eseguito da un gruppo di attività o da un algoritmo parallelo. Un modo consiste nell'utilizzare il meccanismo di annullamento che viene fornito per il [Concurrency:: task_group](../Topic/task_group%20Class.md) e [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) classi. L'altro consiste nel generare un'eccezione nel corpo di una funzione lavoro dell'attività. Il meccanismo di annullamento è più efficace della gestione delle eccezioni per annullare un albero di lavoro parallelo. Oggetto *albero di lavoro parallelo* è un gruppo di gruppi di attività correlate in cui alcuni gruppi di attività contengono altri gruppi di attività. Il meccanismo di annullamento annulla un gruppo di attività e i relativi gruppi di attività figlio dall'alto verso il basso. La gestione delle eccezioni funziona invece in ordine sequenziale dal basso verso l'alto e deve annullare ogni gruppo di attività figlio in modo indipendente in quanto l'eccezione si propaga verso l'alto.  
  
 Quando si lavora direttamente con un oggetto gruppo di attività, utilizzare il [concurrency::task_group::cancel](../Topic/task_group::cancel%20Method.md) o [Concurrency](../Topic/structured_task_group::cancel%20Method.md) metodi per annullare il lavoro che appartiene a questo gruppo di attività. Per annullare un algoritmo parallelo, ad esempio `parallel_for`, creare un gruppo di attività padre e annullarlo. Si consideri ad esempio la funzione seguente, `parallel_find_any`, che esegue la ricerca di un valore in una matrice in parallelo.  
  
 [!code-cpp[concrt-parallel-array-search#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_7.cpp)]  
  
 Poiché gli algoritmi paralleli usano i gruppi di attività, quando una delle iterazioni parallele annulla il gruppo di attività padre, viene annullata l'intera attività. Per la versione completa di questo esempio, vedere [procedura: utilizzare l'annullamento per interrompere un ciclo Parallel](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md).  
  
 Anche se il meccanismo di annullamento della gestione delle eccezioni risulta meno efficace per annullare il lavoro parallelo, in alcune situazioni questo sistema è più appropriato. Ad esempio il metodo seguente, `for_all`, esegue in modo ricorsivo una funzione lavoro in ciascun nodo di una struttura `tree`. In questo esempio, il `_children` membro dati è un [std::list](../../standard-library/list-class.md) contenente `tree` oggetti.  
  
 [!code-cpp[concrt-task-tree-search#6](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_8.cpp)]  
  
 Il chiamante del metodo `tree::for_all` può generare un'eccezione se non richiede che la funzione lavoro venga chiamata per ciascun elemento della struttura ad albero. Nell'esempio seguente viene illustrata la funzione `search_for_value` che cerca un valore nell'oggetto `tree` fornito. La funzione `search_for_value` usa una funzione lavoro che genera un'eccezione quando l'elemento corrente della struttura ad albero corrisponde al valore fornito. La funzione `search_for_value` usa un blocco `try-catch` per acquisire l'eccezione e stampare il risultato nella console.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_9.cpp)]  
  
 Per la versione completa di questo esempio, vedere [procedura: utilizzare eccezioni per interrompere un ciclo Parallel](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 Per ulteriori informazioni sull'annullamento e meccanismi di gestione delle eccezioni che vengono forniti dalla libreria PPL, vedere [annullamento](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl) e [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-nameobject-destructiona-understand-how-cancellation-and-exception-handling-affect-object-destruction"></a><a name="object-destruction"></a> Comprendere come annullamento e la gestione delle eccezioni influiscono sui eliminazione degli oggetti  
 In un albero di lavoro parallelo l'annullamento di un'attività impedisce l'esecuzione delle attività figlio. Ciò può comportare problemi se una delle attività figlio esegue un'operazione importante per l'applicazione, ad esempio liberare una risorsa. L'annullamento delle attività può inoltre provocare la propagazione di un'eccezione tramite un distruttore di oggetti e causare un comportamento non definito nell'applicazione.  
  
 Nell'esempio seguente la classe `Resource` descrive una risorsa e la classe `Container` descrive un contenitore che include le risorse. Nel rispettivo distruttore la classe `Container` chiama il metodo `cleanup` per due dei rispettivi membri `Resource` in parallelo, quindi chiama il metodo `cleanup` per il rispettivo terzo membro `Resource`.  
  
 [!code-cpp[concrt-parallel-resource-destruction#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_10.h)]  
  
 Anche se questo modello non presenta problemi di per sé, si consideri il codice seguente, che esegue due attività in parallelo. La prima attività crea un oggetto `Container`, mentre la seconda annulla l'intera attività.  A scopo illustrativo, nell'esempio vengono utilizzati due [Concurrency:: event](../../parallel/concrt/reference/event-class.md) oggetti per assicurarsi che l'annullamento venga eseguito dopo il `Container` oggetto viene creato e che il `Container` oggetto venga eliminato dopo l'operazione di annullamento.  
  
 [!code-cpp[concrt-parallel-resource-destruction#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_11.cpp)]  
  
 Questo esempio produce il seguente output:  
  
```Output  
Container 1: Freeing resources...Exiting program...  
```  
  
 Nell'esempio di codice sono presenti i problemi seguenti, che possono determinare un comportamento diverso da quello previsto:  
  
-   L'annullamento dell'attività padre determina l'attività figlio, la chiamata a [Concurrency:: parallel_invoke](../Topic/parallel_invoke%20Function.md), deve anche essere annullata. Di conseguenza, queste due risorse non vengono liberate.  
  
-   L'annullamento dell'attività padre comporta la generazione di un'eccezione interna da parte dell'attività figlio.  Poiché il distruttore `Container` non gestisce questa eccezione, l'eccezione viene propagata verso l'alto e la terza risorsa non viene liberata.  
  
-   L'eccezione che viene generata dall'attività figlio si propaga mediante il distruttore `Container`. La generazione da un distruttore imposta l'applicazione su uno stato non definito.  
  
 Si consiglia di non eseguire operazioni critiche nelle attività, ad esempio liberare risorse, a meno che non sia possibile garantire che queste attività non verranno annullate. Si consiglia inoltre di non usare la funzionalità di runtime che può generare un'eccezione nel distruttore dei tipi.  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-namerepeated-blockinga-do-not-block-repeatedly-in-a-parallel-loop"></a><a name="repeated-blocking"></a> Non si bloccano più volte in un ciclo Parallel  
 Un ciclo parallelo, come [Concurrency:: parallel_for](../Topic/parallel_for%20Function.md) o [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) dominato bloccando le operazioni possono comportare il runtime creare molti thread in breve tempo.  
  
 Il runtime di concorrenza esegue lavoro aggiuntivo quando un'attività termina oppure si blocca o cede volontariamente il controllo. Quando un'iterazione del ciclo parallelo si blocca, è possibile che il runtime avvii un'altra iterazione. Quando non sono disponibili thread inattivi, il runtime crea un nuovo thread.  
  
 Se il corpo di un ciclo parallelo si blocca occasionalmente, questo meccanismo contribuisce a ottimizzare la velocità dell'intera attività. Quando invece si blocca un numero elevato di iterazioni, il runtime potrebbe creare un numero elevato di thread per eseguire il lavoro aggiuntivo. Ciò può determinare condizioni di memoria insufficiente o di uso non appropriato delle risorse hardware.  
  
 Si consideri l'esempio seguente che chiama il [Concurrency:: Send](../Topic/send%20Function.md) funzione in ogni iterazione di un `parallel_for` ciclo. Poiché `send` si blocca in modo cooperativo, il runtime crea un nuovo thread per eseguire il lavoro aggiuntivo ogni volta che viene chiamato il metodo `send`.  
  
 [!code-cpp[concrt-repeated-blocking#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_12.cpp)]  
  
 È consigliabile effettuare il refactoring del codice per evitare questo modello. In questo esempio è possibile evitare la creazione di thread aggiuntivi chiamando il metodo `send` in un ciclo seriale di `for`.  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-nameblockinga-do-not-perform-blocking-operations-when-you-cancel-parallel-work"></a><a name="blocking"></a> Non eseguire operazioni di blocco quando si annulla un lavoro parallelo  
 Quando possibile, eseguire le operazioni di blocco prima di chiamare il [concurrency::task_group::cancel](../Topic/task_group::cancel%20Method.md) o [Concurrency](../Topic/structured_task_group::cancel%20Method.md) metodo per annullare un lavoro parallelo.  
  
 Quando tramite un'attività viene effettuata un'operazione di blocco, mediante il runtime può essere eseguito altro lavoro mentre la prima attività resta in attesa dei dati. Quando si sblocca, il runtime ripianifica l'attività di attesa.  Il runtime generalmente ripianifica prima le ultime attività sbloccate e poi quelle sbloccate meno di recente. Pertanto, il runtime potrebbe pianificare lavoro non necessario durante l'operazione di blocco, determinando una riduzione delle prestazioni. Di conseguenza, quando si esegue un'operazione di blocco prima di annullare lavoro parallelo, l'operazione di blocco può ritardare la chiamata a `cancel`. Ciò comporta l'intervento di altre attività per l'esecuzione del lavoro non necessario.  
  
 Si consideri l'esempio seguente che definisce la funzione `parallel_find_answer`. Tale funzione esegue la ricerca di un elemento della matrice fornita che soddisfa la funzione predicato specificata. Quando la funzione predicato restituisce `true`, la funzione lavoro parallelo crea un oggetto `Answer` e annulla l'intera attività.  
  
 [!code-cpp[concrt-blocking-cancel#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_13.cpp)]  
  
 L'operatore `new` esegue un'allocazione per l'heap, che potrebbe bloccarsi. Il runtime esegue altro lavoro solo quando l'attività viene eseguita una chiamata, ad esempio una chiamata di blocco cooperativo [concurrency::critical_section::lock](../Topic/critical_section::lock%20Method.md).  
  
 Nell'esempio seguente viene mostrato come evitare il lavoro non necessario e migliorare in tal modo le prestazioni. Questo esempio annulla il gruppo di attività prima di allocare lo spazio di archiviazione per l'oggetto `Answer`.  
  
 [!code-cpp[concrt-blocking-cancel#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_14.cpp)]  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-nameshared-writesa-do-not-write-to-shared-data-in-a-parallel-loop"></a><a name="shared-writes"></a> Non scrivere ai dati condivisi in un ciclo Parallel  
 Il Runtime di concorrenza fornisce diverse strutture di dati, ad esempio, [Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md), che sincronizza l'accesso simultaneo ai dati condivisi. Queste strutture di dati sono utili in molti casi, ad esempio quando più attività richiedono raramente l'accesso condiviso a una risorsa.  
  
 Nell'esempio seguente viene utilizzata la [Concurrency:: parallel_for_each](../Topic/parallel_for_each%20Function.md) algoritmo e un `critical_section` oggetto per calcolare il conteggio dei numeri primi in un [std:: Array](../../standard-library/array-class-stl.md) oggetto. Questo esempio non è scalabile poiché ogni thread deve attendere per accedere alla variabile condivisa `prime_sum`.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_15.cpp)]  
  
 L'esempio può inoltre comportare una riduzione delle prestazioni in quanto l'operazione di blocco frequente serializza il ciclo in modo efficace.  Inoltre, quando un oggetto runtime di concorrenza esegue un'operazione di blocco, l'utilità di pianificazione potrebbe creare un thread aggiuntivo per eseguire altro lavoro mentre il primo thread rimane in attesa dei dati.  Se il runtime crea numerosi thread perché molte attività sono in attesa dei dati condivisi, è possibile che le prestazioni dell'applicazione si riducano notevolmente o che si passi a uno stato di risorse insufficienti.  
  
 La libreria PPL definisce le [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) (classe), che consente di eliminare lo stato condiviso fornendo accesso alle risorse condivise in una modalità senza blocchi. La classe `combinable` fornisce l'archiviazione locale dei thread che consente di eseguire calcoli accurati e quindi di unire i calcoli in un risultato finale. È possibile considerare un oggetto `combinable` come una variabile di riduzione.  
  
 Nell'esempio seguente si modifica l'esempio precedente mediante l'uso di un oggetto `combinable` anziché un oggetto `critical_section` per calcolare la somma. Questo esempio è scalabile, in quanto ogni thread è responsabile della propria copia locale della somma. Questo esempio viene utilizzato il [concurrency::combinable::combine](../Topic/combinable::combine%20Method.md) metodo per unire i calcoli locali nel risultato finale.  
  
 [!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_16.cpp)]  
  
 Per la versione completa di questo esempio, vedere [procedura: utilizzare la classe combinable per migliorare le prestazioni](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md). Per ulteriori informazioni sulla `combinable` classe, vedere [contenitori e oggetti paralleli](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-namefalse-sharinga-when-possible-avoid-false-sharing"></a><a name="false-sharing"></a> Quando possibile, evitare di condividere False  
 *Condivisione false* si verifica quando più attività simultanee in esecuzione su processori separati scrivono le variabili che si trovano nella stessa riga della cache. Quando una sola attività scrive in una delle variabili, viene invalidata la riga della cache per entrambe le variabili. Ogni processore deve ricaricare la riga della cache ogni volta che questa viene invalidata. Pertanto, la falsa condivisione può compromettere le prestazioni nell'applicazione.  
  
 Nell'esempio di base seguente vengono illustrate due attività simultanee, ognuna delle quali incrementa una variabile di contatore condivisa.  
  
 [!code-cpp[concrt-false-sharing#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_17.cpp)]  
  
 Per eliminare la condivisione dei dati tra le due attività, è possibile modificare l'esempio in modo che vengano usate due variabili di contatore. Questo esempio calcola il valore di contatore finale dopo che le attività sono state completate. L'esempio rappresenta tuttavia un caso di falsa condivisione poiché le variabili `count1` e `count2` possono essere collocate nella stessa riga della cache.  
  
 [!code-cpp[concrt-false-sharing#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_18.cpp)]  
  
 Un modo per eliminare la falsa condivisione consiste nell'assicurarsi che le variabili di contatore si trovino su righe della cache separate. Nell'esempio seguente le variabili `count1` e `count2` vengono allineate su limiti di 64 byte.  
  
 [!code-cpp[concrt-false-sharing#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_19.cpp)]  
  
 In questo esempio si presuppone che la dimensione della cache in memoria sia pari o inferiore a 64 byte.  
  
 Si consiglia di utilizzare il [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) classe quando è necessario condividere dati tra le attività. La classe `combinable` consente di creare le variabili di thread locali in modo da ridurre la probabilità che si verifichi la falsa condivisione. Per ulteriori informazioni sulla `combinable` classe, vedere [contenitori e oggetti paralleli](../../parallel/concrt/parallel-containers-and-objects.md).  
  
 [[Torna all'inizio](#top)]  
  
##  <a name="a-namelifetimea-make-sure-that-variables-are-valid-throughout-the-lifetime-of-a-task"></a><a name="lifetime"></a> Assicurarsi che le variabili siano valide per tutta la durata di un'attività  
 Quando si fornisce un'espressione lambda per un gruppo di attività o un algoritmo parallelo, la clausola di acquisizione specifica se il corpo dell'espressione lambda accede alle variabili nell'ambito di inclusione in base al valore o al riferimento. Quando si passano le variabili a un'espressione lambda in base al riferimento, è necessario garantire che tale variabile duri fino al completamento dell'attività.  
  
 Si consideri l'esempio seguente, che definisce la classe `object` e la funzione `perform_action`. La funzione `perform_action` crea una variabile `object` ed esegue una determinata azione su tale variabile in modo asincrono. Dal momento che non è sicuro che l'attività venga completata prima che la funzione `perform_action` restituisca un risultato, il programma si arresterà in modo anomalo o seguirà un comportamento non specificato se la variabile `object` viene eliminata durante l'esecuzione dell'attività.  
  
 [!code-cpp[concrt-lambda-lifetime#1](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_20.cpp)]  
  
 A seconda dei requisiti dell'applicazione, è possibile usare una delle tecniche seguenti per garantire che le variabili rimangano valide per l'intera durata di ogni attività.  
  
 Nell'esempio seguente la variabile `object` viene passata all'attività in base al valore. Pertanto, l'attività agisce sulla propria copia della variabile.  
  
 [!code-cpp[concrt-lambda-lifetime#2](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_21.cpp)]  
  
 Poiché la variabile `object` viene passata in base al valore, eventuali modifiche di stato apportate a questa variabile non vengono visualizzate nella copia originale.  
  
 Nell'esempio seguente viene utilizzata la [Concurrency](../Topic/task_group::wait%20Method.md) per verificare che l'attività termini prima che il `perform_action` restituisce.  
  
 [!code-cpp[concrt-lambda-lifetime#3](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_22.cpp)]  
  
 Poiché ora l'attività viene completata prima che la funzione restituisca un risultato, la funzione `perform_action` non si comporta più in modo asincrono.  
  
 Nell'esempio seguente la funzione `perform_action` viene modificata in modo da accettare un riferimento alla variabile `object`. Il chiamante deve garantire che la durata della variabile `object` resti valida fino al termine dell'attività.  
  
 [!code-cpp[concrt-lambda-lifetime#4](../../parallel/concrt/codesnippet/CPP/best-practices-in-the-parallel-patterns-library_23.cpp)]  
  
 È inoltre possibile usare un puntatore per controllare la durata di un oggetto che viene passato a un gruppo di attività o a un algoritmo parallelo.  
  
 Per ulteriori informazioni sulle espressioni lambda, vedere [espressioni Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
 [[Torna all'inizio](#top)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure consigliate per Runtime di concorrenza](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Contenitori e oggetti paralleli](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Algoritmi paralleli](../../parallel/concrt/parallel-algorithms.md)   
 [Annullamento](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation_in_the_ppl)   
 [Gestione delle eccezioni](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Procedura dettagliata: Creazione di una rete di elaborazione delle immagini](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Procedura: utilizzare parallel_invoke per scrivere una Routine di ordinamento parallelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)   
 [Procedura: utilizzare l'annullamento per interrompere un ciclo Parallel](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)   
 [Procedura: utilizzare la classe combinable per migliorare le prestazioni](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)   
 [Procedure consigliate nella libreria di agenti asincroni](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)   
 [Procedure consigliate generali nel Runtime di concorrenza](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
