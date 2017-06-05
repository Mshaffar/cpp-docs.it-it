---
title: Concorrenza Namespace (C++ AMP) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AMP/Concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 38c3154244b163202bcb8e271f96b393231247ca
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="concurrency-namespace-c-amp"></a>Spazio dei nomi Concurrency (C++ AMP)
Fornisce le classi e funzioni che permettono di velocizzare l'esecuzione di codice C++ su hardware di dati in parallelo. Per ulteriori informazioni, vedere [Panoramica di C++ AMP](../cpp-amp-overview.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
namespace Concurrency;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="namespaces"></a>Namespaces  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Spazio dei nomi Concurrency::direct3d](concurrency-direct3d-namespace.md)|Sono disponibili funzioni che supportano l'interoperabilità D3D. Consente l'utilizzo diretto di D3D risorse per il calcolo nel codice AMP e l'utilizzo di risorse create in AMP D3D codice, senza creare copie ridondanti intermedi. È possibile utilizzare C++ AMP per accelerare in modo incrementale le sezioni con uso intensivo delle applicazioni DirectX e utilizzare l'API D3D su dati ottenuti da calcoli AMP.|  
|[Spazio dei nomi Concurrency::fast_math](concurrency-fast-math-namespace.md)|Funzioni di `fast_math` dello spazio dei nomi non sono compatibili con C99. Sono disponibili solo a precisione singola versioni di ogni funzione. Queste funzioni usano le funzioni intrinseche di DirectX, che sono più veloci rispetto alle funzioni corrispondenti nel `precise_math` dello spazio dei nomi e non richiedono il supporto esteso e precisione doppia sull'acceleratore, ma sono meno accurate. Esistono due versioni di ogni funzione per la compatibilità a livello di origine con codice C99. entrambe le versioni accettano e restituiscono valori a precisione singola.|  
|[Spazio dei nomi Concurrency::graphics](concurrency-graphics-namespace.md)|Fornisce tipi e funzioni che sono progettate per la programmazione grafica.|  
|[Spazio dei nomi Concurrency::precise_math](concurrency-precise-math-namespace.md)|Funzioni di `precise_math` dello spazio dei nomi sono conformi C99. Sono incluse sia a precisione singola e precisione doppia versioni di ogni funzione. Queste funzioni, ad esempio le funzioni e precisione singola, richiedono il supporto esteso e precisione doppia sull'acceleratore.|  
  
### <a name="classes"></a>Classi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Classe accelerator](accelerator-class.md)|Rappresenta un'astrazione di un nodo di calcolo fisico ottimizzata per il punto di distribuzione.|  
|[Classe accelerator_view](accelerator-view-class.md)|Rappresenta un'astrazione di periferica virtuale su un acceleratore di dati in parallelo di C++ AMP.|  
|[Classe accelerator_view_removed](accelerator-view-removed-class.md)|Eccezione generata quando una chiamata DirectX sottostante ha esito negativo a causa il meccanismo di timeout-rilevamento-e-ripristino di Windows.|  
|[Classe array](array-class.md)|Dati aggregati in un `accelerator_view` nel dominio della griglia. È una raccolta di variabili, uno per ogni elemento in un dominio di griglia. Ogni variabile contiene un valore che corrisponde a un tipo C++.|  
|[Classe array_view](array-view-class.md)|Rappresenta una visualizzazione dei dati in una matrice\<T, N >.|  
|[Classe completion_future](completion-future-class.md)|Rappresenta un futuro che corrisponde a un'operazione asincrona di C++ AMP.|  
|[Classe extent](extent-class.md)|Rappresenta un vettore di valori integer N che specificano i limiti di uno spazio N-dimensionale che presenta un'origine di 0. I valori nel vettore coordinate vengono ordinati dal più significativo al meno significativo. Ad esempio, nello spazio 3D cartesiano, il vettore di extent (7,5,3) rappresenta uno spazio in cui la coordinata z compreso tra 0 e 7, gli intervalli di coordinate y da 0 a 5, e la coordinata x è compreso tra 0 e 3.|  
|[Classe index](index-class.md)|Definisce un punto dell'indice N-dimensionale.|  
|[Classe invalid_compute_domain](invalid-compute-domain-class.md)|L'eccezione generata quando il runtime non è possibile avviare un kernel tramite il dominio di calcolo specificato il `parallel_for_each` sito di chiamata.|  
|[Classe out_of_memory](out-of-memory-class.md)|Eccezione generata quando un metodo non riesce a causa della mancanza di memoria di sistema o dispositivo.|  
|[Classe runtime_exception](runtime-exception-class.md)|Tipo di base per le eccezioni nella libreria di C++ AMP.|  
|[Classe tile_barrier](tile-barrier-class.md)|Una classe di funzionalità che è creabile dal sistema e viene passata a una classe `parallel_for_each` lambda come parte del `tiled_index` parametro. Fornisce un metodo, `wait()`, il cui scopo consiste nel sincronizzare l'esecuzione dei thread sono in esecuzione nel gruppo di thread (sezione).|  
|[Classe tiled_extent](tiled-extent-class.md)|Oggetto `tiled_extent` oggetto è un `extent` oggetto di uno a tre dimensioni che suddivide lo spazio di extent in riquadri unidimensionale bidimensionale e tridimensionale.|  
|[Classe tiled_index](tiled-index-class.md)|Viene fornito un indice in un `tiled_grid` oggetto. Questa classe dispone di proprietà per accedere a elemento di origine locale riquadro e di origine globale.|  
|[Classe uninitialized_object](uninitialized-object-class.md)|Eccezione generata quando viene utilizzato un oggetto non inizializzato.|  
|[Classe unsupported_feature](unsupported-feature-class.md)|Eccezione generata quando viene utilizzata una funzionalità non supportata.|  
  
### <a name="enumerations"></a>Enumerazioni  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Enumerazione access_type](concurrency-namespace-enums-amp.md#access_type)|Specifica il tipo di accesso ai dati.|  
|[Enumerazione queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode)|Specifica le modalità di Accodamento messaggi sono supportate per i tasti di scelta rapida.|  
  
### <a name="operators"></a>Operatori  
  
|Operatore|Descrizione|  
|--------------|-----------------|  
|[operatore Operator = = (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|Determina se le strutture di dati specificati sono uguali.|  
|[operatore! = (operatore) (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|Determina se le strutture di dati specificati sono uguali.|  
|[Operatore operator + (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|Calcola la somma component-wise di argomenti specificati.|  
|[Operatore operator-(C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|Calcola la differenza component-wise tra gli argomenti specificati.|  
|[operatore * (operatore) (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|Calcola il prodotto component-wise di argomenti specificati.|  
|[operatore / (operatore) (C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|Calcola il quoziente component-wise tra gli argomenti specificati.|  
|[Operatore operator % (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|Calcola il modulo del primo argomento specificato dal secondo argomento specificato.|  
  
### <a name="functions"></a>Funzioni  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|Blocca l'esecuzione di tutti i thread in una sezione fino a quando non sono stati completati tutti gli accessi alla memoria.|  
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|Non inizializza il runtime di C++ AMP.|  
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|Di overload. Se il valore archiviato nella posizione specificata risulta uguali per il primo valore specificato, il secondo valore specificato è archiviato nella stessa posizione come operazione atomica.|  
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|Di overload. Imposta il valore archiviato nella posizione specificata sul valore specificato come operazione atomica.|  
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|Di overload. Imposta il valore archiviato nella posizione specificata per la somma di tale valore e un valore specificato come operazione atomica.|  
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|Di overload. Imposta il valore archiviato nella posizione specificata per il bit `and` di tale valore e un valore specificato come operazione atomica.|  
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|Di overload. Decrementa il valore archiviato nella posizione specificata e archivia il risultato nella stessa posizione di un'operazione atomica.|  
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|Di overload. Incrementa il valore archiviato nella posizione specificata e archivia il risultato nella stessa posizione di un'operazione atomica.|  
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|Di overload. Imposta il valore archiviato nella posizione specificata sul valore maggiore di tale valore e un valore specificato come operazione atomica.|  
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|Di overload. Imposta il valore archiviato nella posizione specificata fino al più piccolo di tale valore e un valore specificato come operazione atomica.|  
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|Di overload. Imposta il valore archiviato nella posizione specificata per il bit `or` di tale valore e un valore specificato come operazione atomica.|  
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|Di overload. Imposta il valore archiviato nella posizione specificata per la differenza di tale valore e un valore specificato come operazione atomica.|  
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|Di overload. Imposta il valore archiviato nella posizione specificata per il bit `xor` di tale valore e un valore specificato come operazione atomica.|  
|[copy](concurrency-namespace-functions-amp.md#copy)|Copia un oggetto C++ AMP. Vengono soddisfatti tutti i requisiti di trasferimento di dati sincrono. Impossibile copiare i dati quando viene eseguito codice codice un tasto di scelta rapida. Il formato generale di questa funzione è `copy(src, dest)`.|  
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|Copia un oggetto C++ AMP e restituisce [completion_future](completion-future-class.md) che può essere attesa. Impossibile copiare i dati durante l'esecuzione di codice in un tasto di scelta rapida. Il formato generale di questa funzione è `copy(src, dest)`.|  
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|Interrompe l'esecuzione di una funzione che ha il `restrict(amp)` clausola di restrizione.|  
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|Stampa una stringa formattata di Visual Studio **Output** finestra e genera un [runtime_exception](runtime-exception-class.md) eccezione che ha la stessa formattazione della stringa.|  
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Stampa una stringa formattata di Visual Studio **Output** finestra. Viene chiamato da una funzione che ha il `restrict(amp)` clausola di restrizione.|  
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|Blocca l'esecuzione di tutti i thread in una sezione fino a quando non accede a tutta la memoria globale sono stati completati.|  
|[Funzione parallel_for_each (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|Esegue una funzione all'interno del dominio di calcolo.|  
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|Blocca l'esecuzione di tutti i thread in una sezione fino a `tile_static` gli accessi alla memoria sono state completate.|  
  
## <a name="constants"></a>Costanti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Costante HLSL_MAX_NUM_BUFFERS](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|Il numero massimo di buffer consentiti da DirectX.|  
|[MODULENAME_MAX_LENGTH (costante)](concurrency-namespace-constants-amp.md#modulename_max_length)|Archivia la lunghezza massima del nome del modulo. Questo valore deve essere lo stesso per il compilatore e runtime.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** amp.h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento (C++ AMP)](reference-cpp-amp.md)



