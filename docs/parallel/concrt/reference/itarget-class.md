---
title: Classe ITarget | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
dev_langs:
- C++
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: 22
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
ms.openlocfilehash: 4bd6b21e274431449c8fac452995dd66fc1aef1b
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="itarget-class"></a>Classe ITarget
La classe `ITarget` corrisponde all'interfaccia per tutti i blocchi di destinazione. I blocchi di destinazione usano messaggi a loro offerti da blocchi `ISource`.  
  
## <a name="syntax"></a>Sintassi  
  
```
template<class T>
class ITarget;
```  
  
#### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati del payload all'interno dei messaggi accettati dal blocco di destinazione.  
  
## <a name="members"></a>Membri  
  
### <a name="public-typedefs"></a>Typedef pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`filter_method`|La firma di qualsiasi metodo utilizzato dal blocco che restituisce un `bool` valore per determinare se un messaggio offerto deve essere accettato.|  
|`type`|Un alias del tipo per `T`.|  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[~ Distruttore ITarget](#dtor)|Elimina il `ITarget` oggetto.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[propagazione](#propagate)|Quando sottoposto a override in una classe derivata, passa in modo asincrono un messaggio da un blocco di origine a quello di destinazione.|  
|[Invia](#send)|Quando sottoposto a override in una classe derivata, passa in modo sincrono un messaggio nel blocco di destinazione.|  
|[supports_anonymous_source](#supports_anonymous_source)|Quando viene sottoposto a override in una classe derivata, restituisce true o false a seconda che il blocco dei messaggi accetti messaggi offerti da un'origine che non è collegata a esso. Se tramite il metodo sottoposto a override viene restituito `true`, un messaggio offerto non può essere posticipato dalla destinazione, poiché per l'utilizzo di un messaggio posticipato in un secondo momento viene richiesto che l'origine sia identificata nel Registro di sistema del collegamento di origine.|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[link_source](#link_source)|Quando sottoposto a override in una classe derivata, collega un blocco di origine specificato a questo `ITarget` blocco.|  
|[unlink_source](#unlink_source)|Quando sottoposto a override in una classe derivata, consente di scollegare un blocco di origine specificato da questo `ITarget` blocco.|  
|[unlink_sources](#unlink_sources)|Quando sottoposto a override in una classe derivata, consente di scollegare tutti i blocchi di origine dal `ITarget` blocco.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere [blocchi dei messaggi asincroni](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `ITarget`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** agents.h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="dtor"></a>~ ITarget 

 Elimina il `ITarget` oggetto.  
  
```
virtual ~ITarget();
```  
  
##  <a name="link_source"></a>link_source 

 Quando sottoposto a override in una classe derivata, collega un blocco di origine specificato a questo `ITarget` blocco.  
  
```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_PSource`  
 Il `ISource` blocco collegato a questo `ITarget` blocco.  
  
### <a name="remarks"></a>Note  
 Questa funzione non deve essere chiamata direttamente su un `ITarget` blocco. I blocchi devono essere connesse tra loro tramite il `link_target` metodo `ISource` blocchi che richiameranno il `link_source` metodo sulla destinazione corrispondente.  
  
##  <a name="propagate"></a>propagazione 

 Quando sottoposto a override in una classe derivata, passa in modo asincrono un messaggio da un blocco di origine a quello di destinazione.  
  
```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
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
  
##  <a name="send"></a>Invia 

 Quando sottoposto a override in una classe derivata, passa in modo sincrono un messaggio nel blocco di destinazione.  
  
```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
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
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 Quando viene sottoposto a override in una classe derivata, restituisce true o false a seconda che il blocco dei messaggi accetti messaggi offerti da un'origine che non è collegata a esso. Se tramite il metodo sottoposto a override viene restituito `true`, un messaggio offerto non può essere posticipato dalla destinazione, poiché per l'utilizzo di un messaggio posticipato in un secondo momento viene richiesto che l'origine sia identificata nel Registro di sistema del collegamento di origine.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Valore restituito  
 `true` se il blocco può accettare un messaggio da un'origine che non è collegata a esso; in caso contrario `false`.  
  
##  <a name="unlink_source"></a>unlink_source 

 Quando sottoposto a override in una classe derivata, consente di scollegare un blocco di origine specificato da questo `ITarget` blocco.  
  
```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_PSource`  
 Il `ISource` blocco da scollegare dal `ITarget` blocco.  
  
### <a name="remarks"></a>Note  
 Questa funzione non deve essere chiamata direttamente su un `ITarget` blocco. I blocchi devono essere sconnessi utilizzando il `unlink_target` o `unlink_targets` metodi su `ISource` blocchi che richiameranno il `unlink_source` metodo sulla destinazione corrispondente.  
  
##  <a name="unlink_sources"></a>unlink_sources 

 Quando sottoposto a override in una classe derivata, consente di scollegare tutti i blocchi di origine dal `ITarget` blocco.  
  
```
virtual void unlink_sources() = 0;
```  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [Classe ISource](isource-class.md)
