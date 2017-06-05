---
title: Funzioni &lt;future&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: c542e696e0e5ddef350d40b45fe16f4c3a77882d
ms.contentlocale: it-it
ms.lasthandoff: 04/19/2017

---
# <a name="ltfuturegt-functions"></a>Funzioni &lt;future&gt;
||||  
|-|-|-|  
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|  
|[make_error_condition](#make_error_condition)|[swap](#swap)|  
  
##  <a name="async"></a>  async  
 Rappresenta un  *provider asincrono*.  
  
```
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```  
  
### <a name="parameters"></a>Parametri  
 `policy`  
 Valore [launch](../standard-library/future-enums.md#launch).  
  
### <a name="remarks"></a>Note  
 Definizioni delle abbreviazioni:  
  
|||  
|-|-|  
|*dfn*|Risultato della chiamata a `decay_copy(forward<Fn>(fn))`.|  
|*dargs*|Risultati delle chiamate `decay_copy(forward<ArgsTypes>(args...))`.|  
|*Ty*|Tipo `result_of<Fn(ArgTypes...)>::type`.|  
  
 La prima funzione modello restituisce `async(launch::any, fn, args...)`.  
  
 La seconda funzione restituisce un oggetto `future<Ty>` il cui *stato asincrono associato* include un risultato insieme ai valori di *dfn* e *dargs* e un oggetto thread per gestire un thread di esecuzione separato.  
  
 A meno che `decay<Fn>::type` non sia un tipo diverso da launch, la seconda funzione non fa parte della risoluzione dell'overload.  
  
 Se `policy` è `launch::any`, la funzione potrebbe scegliere `launch::async` o `launch::deferred`. In questa implementazione la funzione usa `launch::async`.  
  
 Se `policy` è `launch::async`, la funzione crea un thread che valuta `INVOKE(dfn, dargs..., Ty)`. La funzione termina dopo aver creato il thread senza attendere i risultati. Se il sistema non riesce ad avviare un nuovo thread, la funzione genera un oggetto [system_error](../standard-library/system-error-class.md) con codice di errore `resource_unavailable_try_again`.  
  
 Se `policy` è `launch::deferred`, la funzione contrassegna il relativo stato asincrono associato come contenente una *funzione posticipata* e termina. La prima chiamata a qualsiasi funzione non temporizzata che attende che lo stato asincrono associato sia ready in effetti chiama la funzione posticipata valutando `INVOKE(dfn, dargs..., Ty)`.  
  
 In tutti i casi, lo stato asincrono associato dell'oggetto `future` non viene impostato su *ready* fino al completamento della valutazione di `INVOKE(dfn, dargs..., Ty)`, indipendentemente dal fatto che venga generata un'eccezione o che la procedura termini normalmente. Il risultato dello stato asincrono associato è un'eccezione se ne è stata generata una oppure qualsiasi valore restituito dalla valutazione.  
  
> [!NOTE]
>  Per un oggetto `future` (o per l'ultimo oggetto [shared_future](../standard-library/shared-future-class.md)) associato a un'attività avviata con `std::async`, il distruttore si blocca se l'attività non è stata completata. In altri termini, si blocca se questo thread non ha ancora chiamato `.get()` o `.wait()` e l'attività è ancora in esecuzione. Se un oggetto `future` ottenuto da `std::async` viene spostato al di fuori dell'ambito locale, l'altro codice che lo usa deve tenere presente che il relativo distruttore può bloccarsi per consentire allo stato condiviso di diventare ready.  
  
 La pseudo-funzione `INVOKE` è definita in [\<functional>](../standard-library/functional.md).  
  
##  <a name="future_category"></a>  future_category  
 Restituisce un riferimento all'oggetto [error_category](../standard-library/error-category-class.md) che caratterizza gli errori associati a oggetti `future`.  
  
```
const error_category& future_category() noexcept;
```  
  
##  <a name="make_error_code"></a>  make_error_code  
 Crea un oggetto [error_code](../standard-library/error-code-class.md) insieme all'oggetto [error_category](../standard-library/error-category-class.md) che caratterizza gli errori [future](../standard-library/future-class.md).  
  
```
inline error_code make_error_code(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>Parametri  
 `Errno`  
 Valore [future_errc](../standard-library/future-enums.md#future_errc) che identifica l'errore segnalato.  
  
### <a name="return-value"></a>Valore restituito  
 `error_code(static_cast<int>(Errno), future_category());`  
  
##  <a name="make_error_condition"></a>  make_error_condition  
 Crea un oggetto [error_condition](../standard-library/error-condition-class.md) insieme all'oggetto [error_category](../standard-library/error-category-class.md) che caratterizza gli errori [future](../standard-library/future-class.md).  
  
```
inline error_condition make_error_condition(future_errc Errno) noexcept;
```  
  
### <a name="parameters"></a>Parametri  
 `Errno`  
 Valore [future_errc](../standard-library/future-enums.md#future_errc) che identifica l'errore segnalato.  
  
### <a name="return-value"></a>Valore restituito  
 `error_condition(static_cast<int>(Errno), future_category());`  
  
##  <a name="swap"></a>  swap  
 Scambia lo *stato asincrono associato* di un oggetto `promise` con quello di un altro oggetto.  
  
```
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```  
  
### <a name="parameters"></a>Parametri  
 `Left`  
 L'oggetto `promise` a sinistra.  
  
 `Right`  
 L'oggetto `promise` corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [\<future>](../standard-library/future.md)



