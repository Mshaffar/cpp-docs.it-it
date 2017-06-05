---
title: Classe target_block | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
dev_langs:
- C++
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
caps.latest.revision: 21
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
ms.openlocfilehash: 2b098523f08345ef366e724c17b6f35211c39e44
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="targetblock-class"></a>Classe target_block
La classe `target_block` corrisponde a una classe base astratta che mette a disposizione la funzionalità di gestione dei collegamenti di base e il controllo degli errori per blocchi di sola destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```  
  
#### <a name="parameters"></a>Parametri  
 `_SourceLinkRegistry`  
 Il Registro di sistema del collegamento da utilizzare per mantenere i collegamenti di origine.  
  
 `_MessageProcessorType`  
 Il tipo di processore per l'elaborazione dei messaggi.  
  
## <a name="members"></a>Membri  
  
### <a name="public-typedefs"></a>Typedef pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`source_iterator`|Il tipo di iteratore per la `source_link_manager` per questo `target_block` oggetto.|  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[target_block](#ctor)|Costruisce un oggetto `target_block`.|  
|[~ target_block distruttore](#dtor)|Elimina il `target_block` oggetto.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[propagazione](#propagate)|Passare in modo asincrono un messaggio da un blocco di origine a quello di destinazione.|  
|[Invia](#send)|Passare in modo sincrono un messaggio da un blocco di origine a quello di destinazione.|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[async_send](#async_send)|Invia in modo asincrono un messaggio per l'elaborazione.|  
|[decline_incoming_messages](#decline_incoming_messages)|Indica al blocco che dovrebbero essere rifiutati nuovi messaggi.|  
|[enable_batched_processing](#enable_batched_processing)|Abilita l'elaborazione batch per questo blocco.|  
|[initialize_target](#initialize_target)|Inizializza l'oggetto di base. In particolare, il `message_processor` oggetto deve essere inizializzato.|  
|[link_source](#link_source)|Collega un blocco di origine specificato a questo `target_block` oggetto.|  
|[process_input_messages](#process_input_messages)|Elabora i messaggi ricevuti come input.|  
|[process_message](#process_message)|Quando sottoposto a override in una classe derivata, elabora un messaggio che è stato accettato dall'oggetto `target_block`.|  
|[propagate_message](#propagate_message)|Quando sottoposto a override in una classe derivata, questo metodo passa in modo asincrono un messaggio da un `ISource` questo blocco `target_block` oggetto. Viene richiamato dal `propagate` metodo, quando viene chiamato da un blocco di origine.|  
|[register_filter](#register_filter)|Registra un metodo di filtro che verrà richiamato su ogni messaggio ricevuto.|  
|[remove_sources](#remove_sources)|Consente di scollegare tutte le origini dopo aver atteso il completamento delle operazioni di invio asincrono in sospeso.|  
|[send_message](#send_message)|Quando sottoposto a override in una classe derivata, questo metodo passa in modo sincrono un messaggio da un `ISource` questo blocco `target_block` oggetto. Viene richiamato dal `send` metodo, quando viene chiamato da un blocco di origine.|  
|[sync_send](#sync_send)|In modo sincrono, inviare un messaggio per l'elaborazione.|  
|[unlink_source](#unlink_source)|Consente di scollegare un blocco di origine specificato da questo `target_block` oggetto.|  
|[unlink_sources](#unlink_sources)|Consente di scollegare tutti i blocchi di origine dal `target_block` oggetto. (Esegue l'override di [ITarget:: Unlink_sources](itarget-class.md#unlink_sources).)|  
|[wait_for_async_sends](#wait_for_async_sends)|Attende che tutte le propagazioni asincrone completare.|  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [ITarget](itarget-class.md)  
  
 `target_block`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** agents.h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="async_send"></a>async_send 

 Invia in modo asincrono un messaggio per l'elaborazione.  
  
```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
 Puntatore al messaggio inviato.  
  
##  <a name="decline_incoming_messages"></a>decline_incoming_messages 

 Indica al blocco che dovrebbero essere rifiutati nuovi messaggi.  
  
```
void decline_incoming_messages();
```  
  
### <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal distruttore per garantire che vengano rifiutati nuovi messaggi mentre l'eliminazione è in corso.  
  
##  <a name="enable_batched_processing"></a>enable_batched_processing 

 Abilita l'elaborazione batch per questo blocco.  
  
```
void enable_batched_processing();
```  
  
##  <a name="initialize_target"></a>initialize_target 

 Inizializza l'oggetto di base. In particolare, il `message_processor` oggetto deve essere inizializzato.  
  
```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```  
  
### <a name="parameters"></a>Parametri  
 `_PScheduler`  
 L'utilità di pianificazione da utilizzare per la pianificazione di attività.  
  
 `_PScheduleGroup`  
 Il gruppo di pianificazione da utilizzare per la pianificazione di attività.  
  
##  <a name="link_source"></a>link_source 

 Collega un blocco di origine specificato a questo `target_block` oggetto.  
  
```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametri  
 `_PSource`  
 Un puntatore per il `ISource` blocco che deve essere collegato.  
  
### <a name="remarks"></a>Note  
 Questa funzione non deve essere chiamata direttamente su un `target_block` oggetto. I blocchi devono essere connesse tra loro tramite il `link_target` metodo `ISource` blocchi che richiameranno il `link_source` metodo sulla destinazione corrispondente.  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Elabora i messaggi ricevuti come input.  
  
```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
  
##  <a name="process_message"></a>process_message 

 Quando sottoposto a override in una classe derivata, elabora un messaggio che è stato accettato dall'oggetto `target_block`.  
  
```
virtual void process_message(message<_Source_type> *);
```  
  
##  <a name="propagate"></a>propagazione 

 Passare in modo asincrono un messaggio da un blocco di origine a quello di destinazione.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
 Puntatore all'oggetto `message`.  
  
 `_PSource`  
 Puntatore al blocco di origine del messaggio di offerta.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [message_status](concurrency-namespace-enums.md) indicazione di ciò che la destinazione ha deciso di fare con il messaggio.  
  
### <a name="remarks"></a>Note  
 Il metodo genera un [invalid_argument](../../../standard-library/invalid-argument-class.md) eccezione se il valore di `_PMessage` o `_PSource` parametro `NULL`.  
  
##  <a name="propagate_message"></a>propagate_message 

 Quando sottoposto a override in una classe derivata, questo metodo passa in modo asincrono un messaggio da un `ISource` questo blocco `target_block` oggetto. Viene richiamato dal `propagate` metodo, quando viene chiamato da un blocco di origine.  
  
```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
 Puntatore all'oggetto `message`.  
  
 `_PSource`  
 Puntatore al blocco di origine del messaggio di offerta.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [message_status](concurrency-namespace-enums.md) indicazione di ciò che la destinazione ha deciso di fare con il messaggio.  
  
##  <a name="register_filter"></a>register_filter 

 Registra un metodo di filtro che verrà richiamato su ogni messaggio ricevuto.  
  
```
void register_filter(filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Parametri  
 `_Filter`  
 Il metodo di filtro.  
  
##  <a name="remove_sources"></a>remove_sources 

 Consente di scollegare tutte le origini dopo aver atteso il completamento delle operazioni di invio asincrono in sospeso.  
  
```
void remove_sources();
```  
  
### <a name="remarks"></a>Note  
 Tutti i blocchi di destinazione devono chiamare questa routine per rimuovere le origini nel distruttore.  
  
##  <a name="send"></a>Invia 

 Passare in modo sincrono un messaggio da un blocco di origine a quello di destinazione.  
  
```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
 Puntatore all'oggetto `message`.  
  
 `_PSource`  
 Puntatore al blocco di origine del messaggio di offerta.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [message_status](concurrency-namespace-enums.md) indicazione di ciò che la destinazione ha deciso di fare con il messaggio.  
  
### <a name="remarks"></a>Note  
 Il metodo genera un [invalid_argument](../../../standard-library/invalid-argument-class.md) eccezione se il valore di `_PMessage` o `_PSource` parametro `NULL`.  
  
 Utilizzo di `send` metodo all'esterno di inizio del messaggio e per propagare i messaggi all'interno di una rete è pericoloso e può causare un deadlock.  
  
 Quando `send` restituisce, il messaggio sia già stato accettato e trasferito nel blocco di destinazione oppure è stata rifiutata dalla destinazione.  
  
##  <a name="send_message"></a>send_message 

 Quando sottoposto a override in una classe derivata, questo metodo passa in modo sincrono un messaggio da un `ISource` questo blocco `target_block` oggetto. Viene richiamato dal `send` metodo, quando viene chiamato da un blocco di origine.  
  
```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [message_status](concurrency-namespace-enums.md) indicazione di ciò che la destinazione ha deciso di fare con il messaggio.  
  
### <a name="remarks"></a>Note  
 Per impostazione predefinita, questo blocco restituisce `declined` a meno che non viene sottoposto a override da una classe derivata.  
  
##  <a name="sync_send"></a>sync_send 

 In modo sincrono, inviare un messaggio per l'elaborazione.  
  
```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
 Puntatore al messaggio inviato.  
  
##  <a name="ctor"></a>target_block 

 Costruisce un oggetto `target_block`.  
  
```
target_block();
```  
  
##  <a name="dtor"></a>~ target_block 

 Elimina il `target_block` oggetto.  
  
```
virtual ~target_block();
```  
  
##  <a name="unlink_source"></a>unlink_source 

 Consente di scollegare un blocco di origine specificato da questo `target_block` oggetto.  
  
```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```  
  
### <a name="parameters"></a>Parametri  
 `_PSource`  
 Un puntatore per il `ISource` blocco che deve essere scollegato.  
  
##  <a name="unlink_sources"></a>unlink_sources 

 Consente di scollegare tutti i blocchi di origine dal `target_block` oggetto.  
  
```
virtual void unlink_sources();
```  
  
##  <a name="wait_for_async_sends"></a>wait_for_async_sends 

 Attende che tutte le propagazioni asincrone completare.  
  
```
void wait_for_async_sends();
```  
  
### <a name="remarks"></a>Note  
 Questo metodo viene utilizzato per i distruttori di blocco di messaggio per garantire che tutte le operazioni asincrone hanno avuto tempo per il completamento prima di eliminare il blocco.  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [Classe ITarget](itarget-class.md)
