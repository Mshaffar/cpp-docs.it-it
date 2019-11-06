---
title: 'C++Informazioni dettagliate sulla compilazione: informazioni di riferimento sulle visualizzazioni di Windows Performance Analyzer'
description: Informazioni di C++ riferimento sulle visualizzazioni di build Insights disponibili in Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e574e7ef4c1b4c5832785d69dbc90ba043cf996a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633091"
---
# <a name="c-build-insights-windows-performance-analyzer-views-reference"></a>C++Informazioni dettagliate sulla compilazione: informazioni di riferimento sulle visualizzazioni di Windows Performance Analyzer

::: moniker range="<=vs-2017"

Gli C++ strumenti di build Insights sono disponibili in Visual Studio 2019. Per visualizzare la documentazione relativa a tale versione, impostare il controllo selettore di versione di Visual Studio per questo articolo su Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

Questo articolo fornisce informazioni dettagliate su ognuna delle C++ visualizzazioni di build Insights disponibili in Windows Performance Analyzer (WPA). Utilizzare questa pagina per trovare:

- descrizioni delle colonne di dati; e
- set di impostazioni disponibili per ogni visualizzazione, inclusi l'uso previsto e la modalità di visualizzazione preferita.

Se non si ha familiarità con WPA, è consigliabile acquisire familiarità con le [nozioni di base di C++ WPA per Build Insights](wpa-basics.md).

## <a name="build-explorer"></a>Esplora compilazione

La visualizzazione Build Explorer viene utilizzata per:

- diagnosticare i problemi di parallelismo,
- determinare se il tempo di compilazione è dominato dall'analisi, dalla generazione del codice o dal collegamento e
- identificare i colli di bottiglia e le attività di compilazione insolitamente lunghe.

### <a name="build-explorer-view-data-columns"></a>Colonne di dati della visualizzazione Esplora compilazione

| Nome colonna | Descrizione |
|-|-|
| BuildTimelineDescription | Descrizione testuale della sequenza temporale in cui si verifica l'attività o la proprietà corrente. |
| BuildTimelineId          | Identificatore in base zero per la sequenza temporale in cui si verifica l'attività o la proprietà corrente. |
| Componente                | Componente da compilare o collegare quando è stato generato l'evento corrente. Il valore di questa colonna è *\<la chiamata X Info\>* quando nessun componente è associato a questo evento. X è un identificatore numerico univoco per la chiamata eseguita nel momento in cui è stato generato l'evento. Questo identificatore corrisponde a quello della colonna InvocationId per questo evento. |
| Conteggio                    | Numero di attività o proprietà rappresentate da questa riga di dati. Questo valore è sempre 1 ed è utile solo negli scenari di aggregazione quando vengono raggruppate più righe. |
| ExclusiveCPUTime         | Quantità di tempo di CPU in millisecondi utilizzata dall'attività. Il tempo impiegato nelle attività figlio non è incluso in questa quantità. |
| ExclusiveDuration        | Durata in millisecondi dell'attività. La durata delle attività figlio non è inclusa in questa quantità. |
| InclusiveCPUTime         | Quantità di tempo di CPU in millisecondi utilizzata da questa attività e da tutte le attività figlio. |
| InclusiveDuration        | Durata in millisecondi di questa attività, incluse tutte le attività figlio. |
| InvocationDescription    | Descrizione testuale della chiamata in cui si è verificato questo evento. La descrizione comprende se è *CL. exe* o *link. exe*e un identificatore di chiamata numerica univoco. Se applicabile, include il percorso completo del componente compilato o collegato durante la chiamata. Per le chiamate che non compilano alcun componente o per quelle che compilano più componenti, il percorso è vuoto. L'identificatore di chiamata corrisponde a quello della colonna InvocationId. |
| InvocationId             | Identificatore numerico univoco per la chiamata in cui si è verificato questo evento. |
| Name                     | Nome dell'attività o della proprietà rappresentata da questo evento. |
| Ora                     | Timestamp che identifica il momento in cui si è verificato l'evento. |
| Strumento                     | Lo strumento in esecuzione quando si è verificato questo evento. Il valore di questa colonna è CL o link. |
| Digitare                     | Tipo dell'evento corrente. Questo valore può essere Activity o Property. |
| Value                    | Se l'evento corrente è una proprietà, questa colonna contiene il relativo valore. Questa colonna viene lasciata vuota quando l'evento corrente è un'attività. |

### <a name="build-explorer-view-presets"></a>Set di impostazioni di visualizzazione di Esplora compilazione

| Nome del set di impostazioni           | Modalità di visualizzazione preferita | Uso |
|-----------------------|---------------------|------------|
| Statistiche attività   | Grafico/tabella       | Utilizzare questo set di impostazioni per visualizzare le statistiche aggregate per tutte le attività di Esplora compilazione. In modalità tabella è necessario sapere a colpo d'occhio se la compilazione è dominata dall'analisi, dalla generazione del codice o dal linker. Le durate aggregate per ogni attività sono ordinate in ordine decrescente. Eseguire il drill-through espandendo il nodo principale per individuare facilmente le chiamate che importano più tempo per queste attività principali. Se lo si desidera, è possibile modificare le impostazioni WPA per visualizzare le medie o altri tipi di aggregazioni. In modalità grafico, vedere quando ogni attività è attiva durante la compilazione. |
| Chiamate           | Graph               | Scorrere verso il basso un elenco di chiamate nella visualizzazione grafico ordinate in base all'ora di inizio. È possibile usarla insieme alla visualizzazione CPU (campionata) per trovare le chiamate che si allineano con le zone di utilizzo della CPU ridotte. Rilevare i problemi di parallelismo. |
| Proprietà di chiamata | Table               | Trovare rapidamente le informazioni chiave su una chiamata del compilatore o del linker specificata. Determinare la versione, la directory di lavoro o la riga di comando completa utilizzata per richiamarla. |
| sequenze temporali             | Graph               | Vedere un grafico a barre relativo alla modalità di parallelismo della compilazione. Identificare a colpo d'occhio i problemi di parallelismo e i colli di bottiglia. Configurare WPA per assegnare significati diversi alle barre in base alle esigenze. Scegliere descrizioni della chiamata come ultima colonna raggruppata per visualizzare un grafico a barre codificato a colori di tutte le chiamate. Consente di identificare rapidamente i colpevoli che richiedono molto tempo. Quindi, eseguire lo zoom avanti e scegliere il nome dell'attività come ultima colonna raggruppata per visualizzare le parti più lunghe. |

## <a name="files"></a>File

La visualizzazione file viene utilizzata per:

- determinare quali intestazioni includono più spesso e
- consente di decidere cosa includere in un'intestazione precompilata (PCH).

### <a name="files-view-data-columns"></a>Colonne di dati della visualizzazione file

| Nome colonna              | Descrizione |
|--------------------------|-------------|
| ActivityName             | Attività in corso quando è stato emesso questo evento di file. Attualmente, questo valore è sempre in fase di *analisi*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Componente                | * |
| Conteggio                    | * |
| Profondità                    | Posizione in base zero nell'albero di inclusione in cui viene trovato il file. Il conteggio inizia dalla radice dell'albero di inclusione. Il valore 0 corrisponde in genere a un file. c/. cpp. |
| ExclusiveDuration        | * |
| IncludedBy               | Percorso completo del file in cui è incluso il file corrente. |
| IncludedPath             | Percorso completo del file corrente. |
| InclusiveDuration        | * |
| InvocationId             | * |
| StartTime                | Timestamp che rappresenta l'ora in cui è stato generato l'evento del file corrente. |
| Strumento                     | * |

\* il valore di questa colonna è uguale a quello della visualizzazione [Build Explorer](#build-explorer-view-data-columns) .

### <a name="files-view-presets"></a>Set di impostazioni di visualizzazione file

| Nome del set di impostazioni | Modalità di visualizzazione preferita | Uso |
|-------------|---------------------|------------|
| Statistiche  | Table               | Vedere i file con il tempo di analisi aggregato più elevato esaminando l'elenco in ordine decrescente. Usare queste informazioni per ristrutturare le intestazioni o decidere quali elementi includere nel file PCH. |

## <a name="functions"></a>Funzioni

La visualizzazione funzioni viene utilizzata per identificare le funzioni con un tempo di generazione del codice troppo lungo.

### <a name="functions-view-data-columns"></a>Colonne di dati della visualizzazione funzioni

| Nome colonna              | Descrizione |
|--------------------------|-------------|
| ActivityName             | Attività in corso quando è stato emesso questo evento di funzione. Attualmente, questo valore è sempre *CodeGeneration*. |
| BuildTimelineDescription | * |
| BuildTimelineId          | * |
| Componente                | * |
| Conteggio                    | * |
| Durata                 | Durata dell'attività di generazione del codice per questa funzione. |
| functionName             | Nome della funzione in fase di generazione del codice. |
| InvocationId             | * |
| StartTime                | Timestamp che rappresenta il momento in cui è stato generato l'evento della funzione corrente. |
| Strumento                     | * |

\* il valore di questa colonna è uguale a quello della visualizzazione [Build Explorer](#build-explorer-view-data-columns) .

### <a name="functions-view-presets"></a>Set di impostazioni di visualizzazione funzioni

| Nome del set di impostazioni | Modalità di visualizzazione preferita | Uso |
|-------------|---------------------|------------|
| Statistiche  | Table               | Vedere le funzioni con il massimo tempo di generazione del codice aggregato esaminando l'elenco in ordine decrescente. Possono suggerire se il codice utilizza la parola chiave **__forceinline** o che alcune funzioni potrebbero essere troppo grandi. |
| sequenze temporali   | Graph               | Esaminare il grafico a barre per apprendere la posizione e la durata delle funzioni che importano più tempo per la generazione. Verificare se sono allineati con colli di bottiglia nella visualizzazione Build Explorer. In caso affermativo, intraprendere le azioni appropriate per ridurre il tempo di generazione del codice e sfruttare i tempi di compilazione. |

## <a name="see-also"></a>Vedere anche

[Introduzione a C++ Build Insights](get-started-with-cpp-build-insights.md)\
\ di [riferimento di vcperf. exe](vcperf-reference.md)
[Nozioni di base su Windows Performance Analyzer](wpa-basics.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end