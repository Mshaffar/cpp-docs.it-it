---
title: Classe ISource | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
dev_langs:
- C++
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
caps.latest.revision: 20
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
ms.openlocfilehash: b5545f666dccb251152dc6c9a83101662848be1c
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="isource-class"></a>Classe ISource
La classe `ISource` corrisponde all'interfaccia per tutti i blocchi di origine. I blocchi di origine propagano messaggi ai blocchi `ITarget`.  
  
## <a name="syntax"></a>Sintassi  
  
```
template<class T>
class ISource;
```  
  
#### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati del payload all'interno dei messaggi generati dal blocco di origine.  
  
## <a name="members"></a>Membri  
  
### <a name="public-typedefs"></a>Typedef pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`source_type`|Un alias del tipo per `T`.|  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[~ Distruttore ISource](#dtor)|Elimina il `ISource` oggetto.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[accettare](#accept)|Quando sottoposto a override in una classe derivata, accetta un messaggio offerto da questo `ISource` blocco, trasferendo la proprietà al chiamante.|  
|[acquire_ref](#acquire_ref)|Quando sottoposto a override in una classe derivata, acquisisce un conteggio dei riferimenti su questo `ISource` blocco, per evitare l'eliminazione.|  
|[Utilizzare](#consume)|Quando sottoposto a override in una classe derivata, utilizza un messaggio precedentemente offerto da questo `ISource` bloccare e riservato correttamente dalla destinazione, trasferendo la proprietà al chiamante.|  
|[link_target](#link_target)|Quando sottoposto a override in una classe derivata, collega un blocco di destinazione al `ISource` blocco.|  
|[release](#release)|Quando sottoposto a override in una classe derivata, rilascia una prenotazione corretta del messaggio precedente.|  
|[release_ref](#release_ref)|Quando sottoposto a override in una classe derivata, rilascia un conteggio dei riferimenti su questo `ISource` blocco.|  
|[reserve](#reserve)|Quando sottoposto a override in una classe derivata, riserva un messaggio precedentemente offerto da questo `ISource` blocco.|  
|[unlink_target](#unlink_target)|Quando sottoposto a override in una classe derivata, consente di scollegare un blocco di destinazione dal `ISource` bloccare, se risulta precedentemente collegato.|  
|[unlink_targets](#unlink_targets)|Quando sottoposto a override in una classe derivata, consente di scollegare tutti i blocchi di destinazione dal `ISource` blocco.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni, vedere [blocchi dei messaggi asincroni](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `ISource`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** agents.h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="accept"></a>accettare 

 Quando sottoposto a override in una classe derivata, accetta un messaggio offerto da questo `ISource` blocco, trasferendo la proprietà al chiamante.  
  
```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` proposto `message` oggetto.  
  
 `_PTarget`  
 Un puntatore al blocco di destinazione che viene eseguita la chiamata di `accept` metodo.  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore al messaggio che il chiamante dispone ora di proprietà.  
  
### <a name="remarks"></a>Note  
 Il `accept` metodo viene chiamato da una destinazione, mentre un messaggio viene offerto da questo `ISource` blocco. Il puntatore del messaggio restituito può essere diverso da quello passato il `propagate` metodo il `ITarget` bloccare, se tale origine creare una copia del messaggio.  
  
##  <a name="acquire_ref"></a>acquire_ref 

 Quando sottoposto a override in una classe derivata, acquisisce un conteggio dei riferimenti su questo `ISource` blocco, per evitare l'eliminazione.  
  
```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_PTarget`  
 Puntatore al blocco di destinazione che chiama questo metodo.  
  
### <a name="remarks"></a>Note  
 Questo metodo viene chiamato da un `ITarget` oggetto collegato a questa origine durante il `link_target` metodo.  
  
##  <a name="consume"></a>Utilizzare 

 Quando sottoposto a override in una classe derivata, utilizza un messaggio precedentemente offerto da questo `ISource` bloccare e riservato correttamente dalla destinazione, trasferendo la proprietà al chiamante.  
  
```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` riservato `message` oggetto.  
  
 `_PTarget`  
 Un puntatore al blocco di destinazione che viene eseguita la chiamata di `consume` metodo.  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore per il `message` che il chiamante dispone ora di proprietà dell'oggetto.  
  
### <a name="remarks"></a>Note  
 Il `consume` metodo è simile a `accept`, ma deve essere sempre preceduto da una chiamata a `reserve` restituito `true`.  
  
##  <a name="dtor"></a>~ ISource 

 Elimina il `ISource` oggetto.  
  
```
virtual ~ISource();
```  
  
##  <a name="link_target"></a>link_target 

 Quando sottoposto a override in una classe derivata, collega un blocco di destinazione al `ISource` blocco.  
  
```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_PTarget`  
 Un puntatore al blocco di destinazione da collegare al `ISource` blocco.  
  
##  <a name="release"></a>versione 

 Quando sottoposto a override in una classe derivata, rilascia una prenotazione corretta del messaggio precedente.  
  
```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` riservato `message` oggetto.  
  
 `_PTarget`  
 Un puntatore al blocco di destinazione che viene eseguita la chiamata di `release` metodo.  
  
##  <a name="release_ref"></a>release_ref 

 Quando sottoposto a override in una classe derivata, rilascia un conteggio dei riferimenti su questo `ISource` blocco.  
  
```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_PTarget`  
 Puntatore al blocco di destinazione che chiama questo metodo.  
  
### <a name="remarks"></a>Note  
 Questo metodo viene chiamato da un `ITarget` oggetto che si sta scollegando dall'origine. Blocco di origine è consentito di rilasciare le risorse riservate per il blocco di destinazione.  
  
##  <a name="reserve"></a>riserva 

 Quando sottoposto a override in una classe derivata, riserva un messaggio precedentemente offerto da questo `ISource` blocco.  
  
```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_MsgId`  
 Il `runtime_object_identity` proposto `message` oggetto.  
  
 `_PTarget`  
 Un puntatore al blocco di destinazione che viene eseguita la chiamata di `reserve` metodo.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il messaggio è stato riservato, `false` in caso contrario. Le prenotazioni possono avere esito negativo per vari motivi, ad esempio: il messaggio era già riservato o accettato da un'altra destinazione, le prenotazioni potrebbero essere negate dall'origine e così via.  
  
### <a name="remarks"></a>Note  
 Dopo aver chiamato `reserve`, se ha esito positivo, è necessario chiamare `consume` o `release` per assumere o rilasciare il possesso del messaggio, rispettivamente.  
  
##  <a name="unlink_target"></a>unlink_target 

 Quando sottoposto a override in una classe derivata, consente di scollegare un blocco di destinazione dal `ISource` bloccare, se risulta precedentemente collegato.  
  
```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```  
  
### <a name="parameters"></a>Parametri  
 `_PTarget`  
 Un puntatore al blocco di destinazione da scollegare dal `ISource` blocco.  
  
##  <a name="unlink_targets"></a>unlink_targets 

 Quando sottoposto a override in una classe derivata, consente di scollegare tutti i blocchi di destinazione dal `ISource` blocco.  
  
```
virtual void unlink_targets() = 0;
```  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [Classe ITarget](itarget-class.md)
