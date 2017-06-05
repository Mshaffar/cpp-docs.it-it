---
title: IUMSThreadProxy (struttura) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
dev_langs:
- C++
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: 19
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
ms.openlocfilehash: 46d486ddccce6f3c54627f3ea96f001e8e3bfcf7
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="iumsthreadproxy-structure"></a>Struttura IUMSThreadProxy
Astrazione per un thread di esecuzione. Se si vuole che all'utilità di pianificazione siano concessi thread UMS, impostare il valore per l'elemento dei criteri dell'utilità di pianificazione `SchedulerKind` su `UmsThreadDefault` e implementare l'interfaccia `IUMSScheduler`. I thread UMS sono supportati solo su sistemi operativi a 64 bit con Windows 7 e versioni successive.  
  
## <a name="syntax"></a>Sintassi  
  
```
struct IUMSThreadProxy : public IThreadProxy;
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[IUMSThreadProxy:: EnterCriticalRegion](#entercriticalregion)|Chiamato per entrare in un'area critica. All'interno di un'area critica, l'utilità di pianificazione non osserverà operazioni asincrone di blocco che si verificano nell'area. Ciò significa che l'utilità di pianificazione verrà non sarà nuovamente immessa per errori di pagina, sospensioni di thread, chiamate asincrone di procedura del kernel (Inizializza) e così via, per un thread UMS.|  
|[IUMSThreadProxy:: EnterHyperCriticalRegion](#enterhypercriticalregion)|Chiamato per entrare in un'area di hyper-critical. All'interno di un'area hyper critica, l'utilità di pianificazione non osserveranno eventuali operazioni di blocco che si verificano nell'area. Pertanto l'utilità di pianificazione non sarà nuovamente immessa per bloccare le chiamate di funzione, i tentativi di acquisizione di blocchi tramite cui vengono eseguiti blocchi, gli errori di pagina, le sospensioni di thread, le chiamate asincrone di procedura del kernel (APC, Asynchronous Procedure Call) e così via, per un thread UMS.|  
|[IUMSThreadProxy:: ExitCriticalRegion](#exitcriticalregion)|Chiamato per uscire da un'area critica.|  
|[IUMSThreadProxy:: ExitHyperCriticalRegion](#exithypercriticalregion)|Chiamato per uscire da un'area hyper critica.|  
|[IUMSThreadProxy:: GetCriticalRegionType](#getcriticalregiontype)|Restituisce il tipo di area critica rientra il proxy del thread. Poiché le aree hyper critici sono un superset di aree critiche, se il codice ha immesso un'area critica e quindi un'area di hyper-critical, `InsideHyperCriticalRegion` verrà restituito.|  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [IThreadProxy](ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** concrtrm. h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="entercriticalregion"></a>Metodo IUMSThreadProxy:: EnterCriticalRegion  
 Chiamato per entrare in un'area critica. All'interno di un'area critica, l'utilità di pianificazione non osserverà operazioni asincrone di blocco che si verificano nell'area. Ciò significa che l'utilità di pianificazione verrà non sarà nuovamente immessa per errori di pagina, sospensioni di thread, chiamate asincrone di procedura del kernel (Inizializza) e così via, per un thread UMS.  
  
```
virtual int EnterCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valore restituito  
 La nuova profondità di area critica. Aree critiche sono rientranti.  
  
##  <a name="enterhypercriticalregion"></a>Metodo IUMSThreadProxy:: EnterHyperCriticalRegion  
 Chiamato per entrare in un'area di hyper-critical. All'interno di un'area hyper critica, l'utilità di pianificazione non osserveranno eventuali operazioni di blocco che si verificano nell'area. Pertanto l'utilità di pianificazione non sarà nuovamente immessa per bloccare le chiamate di funzione, i tentativi di acquisizione di blocchi tramite cui vengono eseguiti blocchi, gli errori di pagina, le sospensioni di thread, le chiamate asincrone di procedura del kernel (APC, Asynchronous Procedure Call) e così via, per un thread UMS.  
  
```
virtual int EnterHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valore restituito  
 La nuova profondità dell'area di hyper-critical. Aree Hyper critiche sono rientranti.  
  
### <a name="remarks"></a>Note  
 L'utilità di pianificazione deve essere particolarmente attenta cosa chiama i metodi e ai blocchi che acquisisce in tali aree. Se i blocchi di codice in tale area su un blocco viene mantenuto attivo da un elemento che l'utilità di pianificazione è responsabile della pianificazione, potrebbe verificarsi deadlock.  
  
##  <a name="exitcriticalregion"></a>Metodo IUMSThreadProxy:: ExitCriticalRegion  
 Chiamato per uscire da un'area critica.  
  
```
virtual int ExitCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valore restituito  
 La nuova profondità di area critica. Aree critiche sono rientranti.  
  
##  <a name="exithypercriticalregion"></a>Metodo IUMSThreadProxy:: ExitHyperCriticalRegion  
 Chiamato per uscire da un'area hyper critica.  
  
```
virtual int ExitHyperCriticalRegion() = 0;
```  
  
### <a name="return-value"></a>Valore restituito  
 La nuova profondità dell'area di hyper-critical. Aree Hyper critiche sono rientranti.  
  
##  <a name="getcriticalregiontype"></a>Metodo IUMSThreadProxy:: GetCriticalRegionType  
 Restituisce il tipo di area critica rientra il proxy del thread. Poiché le aree hyper critici sono un superset di aree critiche, se il codice ha immesso un'area critica e quindi un'area di hyper-critical, `InsideHyperCriticalRegion` verrà restituito.  
  
```
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```  
  
### <a name="return-value"></a>Valore restituito  
 Il tipo di area critica che rientra il proxy del thread.  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [Struttura IUMSScheduler](iumsscheduler-structure.md)
