---
title: Classe progress_reporter | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- progress_reporter
- PPLTASKS/concurrency::progress_reporter
- PPLTASKS/concurrency::progress_reporter::progress_reporter
- PPLTASKS/concurrency::progress_reporter::report
dev_langs:
- C++
helpviewer_keywords:
- progress_reporter class
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: 11
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
ms.openlocfilehash: 98856e26c82d01433e6f8eb0d76110aff1535936
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="progressreporter-class"></a>Classe progress_reporter
La classe del reporter dello stato di avanzamento consente la segnalazione di notifiche di stato di un tipo specifico. Ogni oggetto progress_reporter è associato a una particolare operazione o azione asincrona.  
  
## <a name="syntax"></a>Sintassi  
  
```
template<typename _ProgressType>
class progress_reporter;
```  
  
#### <a name="parameters"></a>Parametri  
 `_ProgressType`  
 Il tipo di payload di ogni notifica dello stato di avanzamento segnalato tramite il reporter dello stato di avanzamento.  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[progress_reporter](#ctor)||  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[report](#report)|Invia un rapporto di stato all'operazione asincrona o all'operazione a cui è associato questo reporter dello stato di avanzamento.|  
  
## <a name="remarks"></a>Note  
 Questo tipo è disponibile solo per le applicazioni Windows Store.  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `progress_reporter`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** ppltasks. h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="ctor"></a>progress_reporter 

```
progress_reporter();
```  
  
##  <a name="report"></a>report 

 Invia un rapporto di stato all'operazione asincrona o all'operazione a cui è associato questo reporter dello stato di avanzamento.  
  
```
void report(const _ProgressType& val) const;
```  
  
### <a name="parameters"></a>Parametri  
 `val`  
 Il payload di report tramite una notifica di stato di avanzamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi concurrency](concurrency-namespace.md)
