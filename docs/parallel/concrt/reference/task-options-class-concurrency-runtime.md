---
title: Classe task_options (Runtime di concorrenza) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppltasks/concurrency::task_options
dev_langs:
- C++
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
caps.latest.revision: 7
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 9b0d7d245ae204fd59715c8142a836adbb63c10a
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="taskoptions-class-concurrency-runtime"></a>Classe task_options (runtime di concorrenza)
Rappresenta le opzioni consentite per la creazione di un'attività  
  
## <a name="syntax"></a>Sintassi  
  
```
class task_options;
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[task_options:: task_options costruttore (Runtime di concorrenza)](#ctor)|Di overload. Elenco predefinito delle opzioni di creazione di attività|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[task_options:: get_cancellation_token (Runtime di concorrenza) (metodo)](#get_cancellation_token)|Restituisce il token di annullamento|  
|[task_options:: get_continuation_context (Runtime di concorrenza) (metodo)](#get_continuation_context)|Restituisce il contesto di continuazione|  
|[task_options:: get_scheduler (Runtime di concorrenza) (metodo)](#get_scheduler)|Restituisce l'utilità di pianificazione|  
|[task_options:: has_cancellation_token (Runtime di concorrenza) (metodo)](#has_cancellation_token)|Indica se un token di annullamento è stato specificato dall'utente|  
|[task_options:: has_scheduler (Runtime di concorrenza) (metodo)](#has_scheduler)|Indica se un'utilità di pianificazione è stata specificata dall'utente|  
|[task_options:: set_cancellation_token (Runtime di concorrenza) (metodo)](#set_cancellation_token)|Imposta il token specificato nelle opzioni|  
|[task_options:: set_continuation_context (Runtime di concorrenza) (metodo)](#set_continuation_context)|Imposta il contesto di continuazione specificato nelle opzioni|  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `task_options`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** ppltasks. h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="get_cancellation_token"></a>task_options:: get_cancellation_token (Runtime di concorrenza) (metodo)  
 Restituisce il token di annullamento  
  
```
cancellation_token get_cancellation_token() const;
```  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="get_continuation_context"></a>task_options:: get_continuation_context (Runtime di concorrenza) (metodo)  
 Restituisce il contesto di continuazione  
  
```
task_continuation_context get_continuation_context() const;
```  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="get_scheduler"></a>task_options:: get_scheduler (Runtime di concorrenza) (metodo)  
 Restituisce l'utilità di pianificazione  
  
```
scheduler_ptr get_scheduler() const;
```  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="has_cancellation_token"></a>task_options:: has_cancellation_token (Runtime di concorrenza) (metodo)  
 Indica se un token di annullamento è stato specificato dall'utente  
  
```
bool has_cancellation_token() const;
```  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="has_scheduler"></a>task_options:: has_scheduler (Runtime di concorrenza) (metodo)  
 Indica se un'utilità di pianificazione è stata specificata dall'utente  
  
```
bool has_scheduler() const;
```  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="set_cancellation_token"></a>task_options:: set_cancellation_token (Runtime di concorrenza) (metodo)  
 Imposta il token specificato nelle opzioni  
  
```
void set_cancellation_token(cancellation_token _Token);
```  
  
### <a name="parameters"></a>Parametri  
 `_Token`  
  
##  <a name="set_continuation_context"></a>task_options:: set_continuation_context (Runtime di concorrenza) (metodo)  
 Imposta il contesto di continuazione specificato nelle opzioni  
  
```
void set_continuation_context(task_continuation_context _ContinuationContext);
```  
  
### <a name="parameters"></a>Parametri  
 `_ContinuationContext`  
  
##  <a name="ctor"></a>task_options:: task_options costruttore (Runtime di concorrenza)  
 Elenco predefinito delle opzioni di creazione di attività  
  
```
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```  
  
### <a name="parameters"></a>Parametri  
 `_SchedType`  
 `_Token`  
 `_ContinuationContext`  
 `_Scheduler`  
 `_TaskOptions`  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)
