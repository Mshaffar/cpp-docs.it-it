---
title: Modelli provider OLE DB (C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: 793aa08630ec92f99c33c2a4f3688e78630a6c58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361256"
---
# <a name="ole-db-provider-templates-c"></a>Modelli provider OLE DB (C++)

OLE DB è una parte importante della strategia di Microsoft Universal Data Access. La progettazione di OLE DB consente l'accesso ai dati ad alte prestazioni da qualsiasi origine dati. I dati tabulari sono visualizzabili tramite OLE DB indipendentemente dal fatto che proviene da un database. La flessibilità ti offre una notevole quantità di energia elettrica.

Come illustrato in [consumer OLE DB e provider](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB Usa il concetto di consumer e provider. Il consumer effettua le richieste per i dati. il provider restituisce i dati in un formato tabulare al consumer. Da una prospettiva di programmazione, l'implicazione più importante di questo modello è che il provider deve implementare tutte le chiamate che dal consumer.

## <a name="what-is-a-provider"></a>Che cos'è un Provider?

Un provider OLE DB è un set di oggetti COM che servono interfaccia chiamate da un oggetto di consumer, il trasferimento dei dati in un formato tabulare da un'origine permanente (denominata archivio dati) per il consumer.

I provider possono essere semplici o complesse. Il provider possa supportare una quantità minima di funzionalità o un provider di qualità di produzione completa implementare più interfacce. Un provider può restituire una tabella, consentono al client determinare il formato della tabella ed eseguire operazioni su tali dati.

Ogni provider implementa un set standard di oggetti COM per gestire le richieste dal client, con un significato standard che eventuali consumer OLE DB possono accedere ai dati da qualsiasi provider, indipendentemente dalla lingua (ad esempio C++ e Basic).

Ogni oggetto COM contiene diverse interfacce, alcuni dei quali sono necessari e alcuni dei quali sono facoltativi. Implementando le interfacce obbligatorie, un provider garantisce un livello minimo di funzionalità (detto conformità) che deve essere in grado di usare qualsiasi client. Un provider può implementare interfacce facoltative per fornire funzionalità aggiuntive. Il [architettura dei modelli Provider OLE DB](../../data/oledb/ole-db-provider-template-architecture.md) descrive queste interfacce in modo dettagliato. Il client deve chiamare sempre `QueryInterface` per determinare se un provider supporta una determinata interfaccia.

## <a name="ole-db-specification-level-support"></a>Supporto a livello di OLE DB specifica

I modelli di provider OLE DB supportano la specifica della versione 2.7 OLE DB. Utilizzare i modelli di provider OLE DB, è possibile implementare un provider conforme a livello 0. Il `Provider` campione, ad esempio, Usa i modelli per implementare un server di comando non-MS-DOS che esegue il comando DIR DOS per eseguire una query nel file system. Il `Provider` esempio restituisce le informazioni sulla directory in un set di righe, ovvero il meccanismo standard OLE DB per la restituzione di dati tabulari.

Il tipo più semplice di provider supportati da modelli OLE DB è un provider di sola lettura con nessun comando. Provider con i comandi sono anche supportate, così come le funzionalità di aggiunta di segnalibri e di lettura/scrittura. È possibile implementare un provider di lettura/scrittura per scrivere codice aggiuntivo. Le transazioni e set di righe dinamici non sono supportate dalla versione corrente, ma è possibile aggiungerli se si desidera.

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Quando devi creare un Provider OLE DB?

Non è sempre necessario creare un proprio provider; Microsoft offre diversi provider standard, preassemblati nel **proprietà di Data Link** finestra di dialogo in Visual C++. Viene eseguita principalmente per creare un provider OLE DB per sfruttare i vantaggi della strategia di Universal Data Access. Alcuni dei vantaggi di tale operazione sono:

- L'accesso ai dati tramite qualsiasi linguaggio, ad esempio C++, Basic e Visual Basic Scripting Edition. Consente ai programmatori diversi all'interno dell'organizzazione di accedere agli stessi dati nello stesso modo, indipendentemente dal fatto che di linguaggio usano.

- Aprire i dati ad altre origini dati, ad esempio SQL Server, Excel e Access. Ciò può essere utile se si desidera trasferire i dati tra formati diversi.

- Che fanno parte di operazioni di cross-zdroj dat (eterogenei). Può trattarsi di un metodo efficace per il data warehousing. Tramite i provider OLE DB, è possibile mantenere i dati nel relativo formato nativo e ancora essere in grado di accedervi in un'operazione semplice.

- Aggiunta di funzionalità aggiuntive ai dati, ad esempio l'elaborazione delle query.

- Miglioramento delle prestazioni di accesso ai dati controllando la modifica.

- Maggiore affidabilità. Se si dispone di un formato dati proprietari che solo un programmatore può accedere, si è a rischio. Utilizzando provider OLE DB, è possibile aprire tale formato proprietario per tutti i programmatori.

## <a name="read-only-and-updatable-providers"></a>Provider aggiornabili e di sola lettura

I provider possono variare significativamente in funzionalità e complessità. È utile suddividere i provider provider aggiornabili e provider di sola lettura:

- Visual C++ 6.0 supportati solo i provider di sola lettura. [Creazione di un Provider OLE DB](../../data/oledb/creating-an-ole-db-provider.md) viene illustrato come creare un provider di sola lettura.
- Visual C++ supporta i provider aggiornabili, che è possono aggiornare (scrivere) nell'archivio dati. Per informazioni sui provider aggiornabili, vedere [creazione di un Provider aggiornabile](../../data/oledb/creating-an-updatable-provider.md); gli [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) esempio è riportato un esempio di un provider aggiornabile.

Per altre informazioni, vedere:

- [L'architettura dei modelli Provider OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)

- [Creazione di un provider OLE DB](../../data/oledb/creating-an-ole-db-provider.md)

- [Programmazione con OLE DB](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>Vedere anche

[Accesso ai dati](../data-access-in-cpp.md)<br/>
[Documentazione di OLE DB SDK](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[guida di riferimento per programmatori OLE DB](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
