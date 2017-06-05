---
title: Classe SchedulerPolicy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
dev_langs:
- C++
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
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
ms.openlocfilehash: a00f7d9cafbd84fc3bbf6b10f322fad6166110cd
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="schedulerpolicy-class"></a>Classe SchedulerPolicy
La classe `SchedulerPolicy` contiene un set di coppie chiave/valore, uno per ogni elemento dei criteri, che controllano il comportamento di un'istanza dell'utilità di pianificazione.  
  
## <a name="syntax"></a>Sintassi  
  
```
class SchedulerPolicy;
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[SchedulerPolicy](#ctor)|Di overload. Costruisce un nuovo criterio dell'utilità di pianificazione e la popola con i valori per [chiavi dei criteri](concurrency-namespace-enums.md) supportato dal Runtime di concorrenza le utilità di pianificazione e Gestione risorse.|  
|[~ Distruttore SchedulerPolicy](#dtor)|Elimina un criterio dell'utilità di pianificazione.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[GetPolicyValue](#getpolicyvalue)|Recupera il valore della chiave di criteri fornito come il `key` parametro.|  
|[SetConcurrencyLimits](#setconcurrencylimits)|Consente di impostare contemporaneamente il `MinConcurrency` e `MaxConcurrency` criteri di `SchedulerPolicy` oggetto.|  
|[SetPolicyValue](#setpolicyvalue)|Imposta il valore della chiave di criteri fornito come il `key` parametro e restituisce il valore precedente.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[operator=](#operator_eq)|Assegna i criteri dell'utilità di pianificazione di un altro criterio dell'utilità di pianificazione.|  
  
## <a name="remarks"></a>Note  
 Per ulteriori informazioni sui criteri che possono essere controllate utilizzando la `SchedulerPolicy` , vedere [PolicyElementKey](concurrency-namespace-enums.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `SchedulerPolicy`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** concrt. h, concrtrm. h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="getpolicyvalue"></a>GetPolicyValue 

 Recupera il valore della chiave di criteri fornito come il `key` parametro.  
  
```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```  
  
### <a name="parameters"></a>Parametri  
 `key`  
 Chiave dei criteri per cui recuperare un valore.  
  
### <a name="return-value"></a>Valore restituito  
 Se la chiave specificata per il `key` parametro è supportato, il valore del criterio per la chiave di cui è stato eseguito il cast a un `unsigned int`.  
  
### <a name="remarks"></a>Note  
 Il metodo genererà [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) per una chiave di criterio non valido.  
  
##  <a name="operator_eq"></a>operatore = 

 Assegna i criteri dell'utilità di pianificazione di un altro criterio dell'utilità di pianificazione.  
  
```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```  
  
### <a name="parameters"></a>Parametri  
 `_RhsPolicy`  
 I criteri da assegnare a questo criterio.  
  
### <a name="return-value"></a>Valore restituito  
 Riferimento ai criteri dell'utilità di pianificazione.  
  
### <a name="remarks"></a>Note  
 Spesso, il modo più semplice per definire nuovi criteri dell'utilità di pianificazione consiste nel copiare i criteri esistenti e nel modificarli tramite i metodi `SetPolicyValue` o `SetConcurrencyLimits`.  
  
##  <a name="ctor"></a>SchedulerPolicy 

 Costruisce un nuovo criterio dell'utilità di pianificazione e la popola con i valori per [chiavi dei criteri](concurrency-namespace-enums.md) supportato dal Runtime di concorrenza le utilità di pianificazione e Gestione risorse.  
  
```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
 ...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```  
  
### <a name="parameters"></a>Parametri  
 `_PolicyKeyCount`  
 Il numero di elementi chiave/valore coppie che seguono il `_PolicyKeyCount` parametro.  
  
 `_SrcPolicy`  
 I criteri di origine da copiare.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore crea nuovi criteri dell'utilità di pianificazione in tutti i criteri verranno inizializzati ai valori predefiniti.  
  
 Il secondo costruttore crea un nuovo criterio dell'utilità di pianificazione che utilizza uno stile di parametro denominato di inizializzazione. I valori dopo il `_PolicyKeyCount` parametro vengono forniti come coppie chiave/valore. Qualsiasi chiave dei criteri che non viene specificata nel costruttore avrà il valore predefinito. Questo costruttore può generare le eccezioni [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) o [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).  
  
 Il terzo costruttore è un costruttore di copia. Spesso, il modo più semplice per definire nuovi criteri dell'utilità di pianificazione consiste nel copiare i criteri esistenti e nel modificarli tramite i metodi `SetPolicyValue` o `SetConcurrencyLimits`.  
  
##  <a name="dtor"></a>~ SchedulerPolicy 

 Elimina un criterio dell'utilità di pianificazione.  
  
```
~SchedulerPolicy();
```  
  
##  <a name="setconcurrencylimits"></a>SetConcurrencyLimits 

 Consente di impostare contemporaneamente il `MinConcurrency` e `MaxConcurrency` criteri di `SchedulerPolicy` oggetto.  
  
```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```  
  
### <a name="parameters"></a>Parametri  
 `_MinConcurrency`  
 Il valore per la `MinConcurrency` chiave dei criteri.  
  
 `_MaxConcurrency`  
 Il valore per la `MaxConcurrency` chiave dei criteri.  
  
### <a name="remarks"></a>Note  
 Il metodo genererà [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) se il valore specificato per il `MinConcurrency` criteri sono maggiori di quello specificato per il `MaxConcurrency` criteri.  
  
 Il metodo può generare [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) per altri valori non validi.  
  
##  <a name="setpolicyvalue"></a>SetPolicyValue 

 Imposta il valore della chiave di criteri fornito come il `key` parametro e restituisce il valore precedente.  
  
```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```  
  
### <a name="parameters"></a>Parametri  
 `key`  
 Impostare un valore per la chiave di criteri.  
  
 `value`  
 Il valore su cui impostare la chiave dei criteri.  
  
### <a name="return-value"></a>Valore restituito  
 Se la chiave specificata per il `key` parametro è supportato, il valore dei criteri precedenti per la chiave di cui è stato eseguito il cast a un `unsigned int`.  
  
### <a name="remarks"></a>Note  
 Il metodo genererà [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) per una chiave di criteri non validi o il cui valore non può essere impostato da un tasto qualsiasi criterio di `SetPolicyValue` metodo.  
  
 Il metodo genererà [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) per un valore che non è supportato per la chiave specificata per il `key` parametro.  
  
 Si noti che questo metodo non è consentito impostare il `MinConcurrency` o `MaxConcurrency` criteri. Per impostare questi valori, utilizzare il [SetConcurrencyLimits](#setconcurrencylimits) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [CurrentScheduler (classe)](currentscheduler-class.md)   
 [Scheduler (classe)](scheduler-class.md)   
 [Utilità di pianificazione](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)



