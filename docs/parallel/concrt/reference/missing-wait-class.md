---
title: Classe missing_wait | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs:
- C++
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
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
ms.openlocfilehash: 70b1c77660992b33de2204fd4f4221ed6e957e21
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="missingwait-class"></a>Classe missing_wait
Questa classe descrive un'eccezione generata quando vi sono attività ancora pianificate per un oggetto `task_group` o `structured_task_group` nel momento di esecuzione del distruttore dell'oggetto. Questa eccezione non sarà mai generata se il distruttore viene raggiunto a causa del processo di rimozione dello stack come risultato di un'eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```
class missing_wait : public std::exception;
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[missing_wait](#ctor)|Di overload. Costruisce un oggetto `missing_wait`.|  
  
## <a name="remarks"></a>Note  
 Se il flusso di eccezione, assente è responsabile per la chiamata al `wait` o `run_and_wait` metodo di un `task_group` o `structured_task_group` oggetto prima di consentire a distruggere quell'oggetto. Il runtime genera questa eccezione per indicare che si dimentica di chiamare il `wait` o `run_and_wait` (metodo).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** concrt  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="ctor"></a>missing_wait 

 Costruisce un oggetto `missing_wait`.  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>Parametri  
 `_Message`  
 Messaggio descrittivo dell'errore.  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [Classe task_group](task-group-class.md)   
 [attesa](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [Classe structured_task_group](structured-task-group-class.md)
