---
title: Classe unbounded_buffer | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 9a9c44985b1e9475b8760d835e2a8fd45361ea5a
ms.lasthandoff: 03/17/2017

---


Un blocco della messaggistica `unbounded_buffer` è un `propagator_block` multi-origine a destinazione singola, in grado di archiviare un numero non associato di messaggi di un tipo diverso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
template<  
   class             _Type  
>  
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;  
```  
  
#### <a name="parameters"></a>Parametri  
 `_Type`  
 Il tipo di payload dei messaggi archiviati e propagati dal buffer.  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[unbounded_buffer](#ctor)|Di overload. Costruisce un `unbounded_buffer` blocco della messaggistica.|  
|[~ unbounded_buffer distruttore](#dtor)|Elimina il `unbounded_buffer` blocco della messaggistica.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[rimuovere dalla coda](#dequeue)|Rimuove un elemento dal `unbounded_buffer` blocco della messaggistica.|  
|[Enqueue](#enqueue)|Aggiunge un elemento per il `unbounded_buffer` blocco della messaggistica.|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[accept_message](#accept_message)|Accetta un messaggio offerto da questo `unbounded_buffer` blocco della messaggistica, trasferendo la proprietà al chiamante.|  
|[consume_message](#consume_message)|Utilizza un messaggio precedentemente offerto dal `unbounded_buffer` blocco della messaggistica e riservato dalla destinazione, trasferendo la proprietà al chiamante.|  
|[link_target_notification](#link_target_notification)|Un callback di notifica che una nuova destinazione è stata collegata a questo `unbounded_buffer` blocco della messaggistica.|  
|[process_input_messages](#process_input_messages)|Posizioni di `message``_PMessage` in questo `unbounded_buffer` blocco della messaggistica e tenta di metterlo a disposizione tutte le destinazioni collegate.|  
|[propagate_message](#propagate_message)|Passare in modo asincrono un messaggio da un `ISource` questo blocco `unbounded_buffer` blocco della messaggistica. Viene richiamato dal `propagate` metodo, quando viene chiamato da un blocco di origine.|  
|[propagate_output_messages](#propagate_output_messages)|Posizioni di `message``_PMessage` in questo `unbounded_buffer` blocco della messaggistica e tenta di metterlo a disposizione tutte le destinazioni collegate. (Esegue l'override di [source_block:: propagate_output_messages](source-block-class.md#propagate_output_messages).)|  
|[release_message](#release_message)|Rilascia una prenotazione messaggio precedente. (Esegue l'override di [source_block:: release_message](source-block-class.md#release_message).)|  
|[reserve_message](#reserve_message)|Consente di riservare un messaggio precedentemente offerto da questo `unbounded_buffer` blocco della messaggistica. (Esegue l'override di [source_block:: reserve_message](source-block-class.md#reserve_message).)|  
|[resume_propagation](#resume_propagation)|Riprende la propagazione dopo una prenotazione è stata rilasciata. (Esegue l'override di [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|  
|[send_message](#send_message)|Passare in modo sincrono un messaggio da un `ISource` questo blocco `unbounded_buffer` blocco della messaggistica. Viene richiamato dal `send` metodo, quando viene chiamato da un blocco di origine.|  
|[supports_anonymous_source](#supports_anonymous_source)|Esegue l'override del metodo `supports_anonymous_source` per indicare che questo blocco può accettare messaggi offerti da un'origine non collegata. (Esegue l'override di [ITarget:: Supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  

 Per ulteriori informazioni, vedere [blocchi dei messaggi asincroni](../asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [ISource](isource-class.md)  
  
 [ITarget](itarget-class.md)  
  
 [source_block](source-block-class.md)  
  
 [propagator_block](propagator-block-class.md)  
  
 `unbounded_buffer`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** agents.h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="accept_message"></a>accept_message 

 Accetta un messaggio offerto da questo `unbounded_buffer` blocco della messaggistica, trasferendo la proprietà al chiamante.  
  
```  
virtual message<_Type> * accept_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` proposto `message` oggetto.  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore per il `message` che il chiamante dispone ora di proprietà dell'oggetto.  
  
##  <a name="consume_message"></a>consume_message 

 Utilizza un messaggio precedentemente offerto dal `unbounded_buffer` blocco della messaggistica e riservato dalla destinazione, trasferendo la proprietà al chiamante.  
  
```  
virtual message<_Type> * consume_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` del `message` dell'oggetto utilizzato.  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore per il `message` che il chiamante dispone ora di proprietà dell'oggetto.  
  
### <a name="remarks"></a>Note  
 Simile a `accept`, ma è sempre preceduto da una chiamata a `reserve`.  
  
##  <a name="dequeue"></a>rimuovere dalla coda 

 Rimuove un elemento dal `unbounded_buffer` blocco della messaggistica.  
  
```  
_Type dequeue();  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il payload del messaggio rimosso il `unbounded_buffer`.  
  
##  <a name="enqueue"></a>Enqueue 

 Aggiunge un elemento per il `unbounded_buffer` blocco della messaggistica.  
  
```  
bool enqueue(  
   _Type const&                 _Item  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_Item`  
 Elemento da aggiungere.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se l'elemento è stato accettato, `false` in caso contrario.  
  
##  <a name="link_target_notification"></a>link_target_notification 

 Un callback di notifica che una nuova destinazione è stata collegata a questo `unbounded_buffer` blocco della messaggistica.  
  
```  
virtual void link_target_notification(  
   _Inout_ ITarget<_Type> *                 _PTarget  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_PTarget`  
 Puntatore alla destinazione appena collegata.  
  
##  <a name="propagate_message"></a>propagate_message 

 Passare in modo asincrono un messaggio da un `ISource` questo blocco `unbounded_buffer` blocco della messaggistica. Viene richiamato dal `propagate` metodo, quando viene chiamato da un blocco di origine.  
  
```  
virtual message_status propagate_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
 Puntatore all'oggetto `message`.  
  
 `_PSource`  
 Puntatore al blocco di origine del messaggio di offerta.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [message_status](concurrency-namespace-enums.md#message_status) indicazione di ciò che la destinazione ha deciso di fare con il messaggio.  
  
##  <a name="propagate_output_messages"></a>propagate_output_messages 

 Posizioni di `message``_PMessage` in questo `unbounded_buffer` blocco della messaggistica e tenta di metterlo a disposizione tutte le destinazioni collegate.  
  
```  
virtual void propagate_output_messages();  
```  
  
### <a name="remarks"></a>Note  
 Se è già un altro messaggio prima di quella di `unbounded_buffer`, verificherà la propagazione alle destinazioni collegate non fino a quando i messaggi precedenti sono stati accettati o utilizzati. La prima destinazione collegata correttamente `accept` o `consume` il messaggio assume la proprietà, e pertanto altre destinazioni non possono ottenere il messaggio.  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Posizioni di `message``_PMessage` in questo `unbounded_buffer` blocco della messaggistica e tenta di metterlo a disposizione tutte le destinazioni collegate.  
  
```  
virtual void process_input_messages(  
   _Inout_ message<_Type> *                 _PMessage  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
  
##  <a name="release_message"></a>release_message 

 Rilascia una prenotazione messaggio precedente.  
  
```  
virtual void release_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` del `message` dell'oggetto viene rilasciato.  
  
##  <a name="reserve_message"></a>reserve_message 

 Consente di riservare un messaggio precedentemente offerto da questo `unbounded_buffer` blocco della messaggistica.  
  
```  
virtual bool reserve_message(  
   runtime_object_identity                 _MsgId  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` del `message` dell'oggetto viene riservato.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il messaggio è stato riservato, `false` in caso contrario.  
  
### <a name="remarks"></a>Note  
 Dopo aver `reserve` viene chiamato, restituisce `true`, ad esempio `consume` o `release` deve essere chiamato per assumere o rilasciare la proprietà del messaggio.  
  
##  <a name="resume_propagation"></a>resume_propagation 

 Riprende la propagazione dopo una prenotazione è stata rilasciata.  
  
```  
virtual void resume_propagation();  
```  
  
##  <a name="send_message"></a>send_message 

 Passare in modo sincrono un messaggio da un `ISource` questo blocco `unbounded_buffer` blocco della messaggistica. Viene richiamato dal `send` metodo, quando viene chiamato da un blocco di origine.  
  
```  
virtual message_status send_message(  
   _Inout_ message<_Type> *                 _PMessage,  
   _Inout_ ISource<_Type> *                 _PSource  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_PMessage`  
 Puntatore all'oggetto `message`.  
  
 `_PSource`  
 Puntatore al blocco di origine del messaggio di offerta.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [message_status](concurrency-namespace-enums.md#message_status) indicazione di ciò che la destinazione ha deciso di fare con il messaggio.  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 Esegue l'override del metodo `supports_anonymous_source` per indicare che questo blocco può accettare messaggi offerti da un'origine non collegata.  
  
```  
virtual bool supports_anonymous_source();  
```  
  
### <a name="return-value"></a>Valore restituito  
 `true` poiché tramite il blocco non vengono posticipati i messaggi offerti.  
  
##  <a name="ctor"></a>unbounded_buffer 

 Costruisce un `unbounded_buffer` blocco della messaggistica.  
  
```  
unbounded_buffer();  
  
unbounded_buffer(  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler  
);  
  
unbounded_buffer(  
   Scheduler&                 _PScheduler,  
   filter_method const&                 _Filter  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup  
);  
  
unbounded_buffer(  
   ScheduleGroup&                 _PScheduleGroup,  
   filter_method const&                 _Filter  
);  
```  
  
### <a name="parameters"></a>Parametri  
 `_Filter`  
 Una funzione di filtro che determina se accettare messaggi offerti.  
  
 `_PScheduler`  
 Il `Scheduler` entro il quale la propagazione delle attività per il `unbounded_buffer` blocco della messaggistica.  
  
 `_PScheduleGroup`  
 Il `ScheduleGroup` entro il quale la propagazione delle attività per il `unbounded_buffer` blocco della messaggistica. L'oggetto `Scheduler` usato è previsto dal gruppo di pianificazione.  
  
### <a name="remarks"></a>Note  
 Se non si specificano i parametri `_PScheduler` o `_PScheduleGroup` , il runtime usa l'utilità di pianificazione predefinita.  
  
 Il tipo di `filter_method` è un funtore con firma `bool (_Type const &)` che viene richiamato da questo `unbounded_buffer` blocco della messaggistica per determinare se è necessario accettare un messaggio offerto.  
  
##  <a name="dtor"></a>~ unbounded_buffer 

 Elimina il `unbounded_buffer` blocco della messaggistica.  
  
```  
~unbounded_buffer();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [Classe overwrite_buffer](overwrite-buffer-class.md)   
 [Classe single_assignment](single-assignment-class.md)


