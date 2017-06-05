---
title: Classe shared_future | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
dev_langs:
- C++
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
caps.latest.revision: 13
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 84b55dc763d4cd254e4aca55c01690ce5abf0152
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="sharedfuture-class"></a>Classe shared_future
Descrive un *oggetto restituito asincrono*. Diversamente da un oggetto [future](../standard-library/future-class.md), un *provider asincrono* può essere associato a un numero qualsiasi di oggetti `shared_future`.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class Ty>
class shared_future;
```  
  
## <a name="remarks"></a>Note  
 Non chiamare alcun metodo diverso da `valid`, `operator=` né il distruttore su un oggetto `shared_future` *vuoto*.  
  
 Gli oggetti `shared_future` non sono sincronizzati. La chiamata di metodi sullo stesso oggetto da più thread introduce una competizione tra dati con risultati imprevisti.  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[shared_future](#shared_future)|Costruisce un oggetto `shared_future`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[get](#get)|Recupera il risultato archiviato nello *stato asincrono associato*.|  
|[valido](#valid)|Specifica se l'oggetto non è vuoto.|  
|[attesa](#wait)|Blocca il thread corrente finché lo stato asincrono associato non è ready.|  
|[wait_for](#wait_for)|Blocca finché lo stato asincrono associato non è ready o finché non trascorre il periodo di tempo specificato.|  
|[wait_until](#wait_until)|Blocca finché lo stato asincrono associato non è ready o fino al momento specificato.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[shared_future::operator=](#op_eq)|Assegna un nuovo stato asincrono associato.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<futura >  
  
 **Spazio dei nomi:** std  
  
##  <a name="get"></a>shared_future:: Get
 Recupera il risultato archiviato nello *stato asincrono associato*.  
  
```
const Ty& get() const;

Ty& get() const;

void get() const;
```  
  
### <a name="remarks"></a>Note  
 Se il risultato è un'eccezione, il metodo la genera nuovamente. In caso contrario, viene restituito il risultato.  
  
 Prima di recuperare il risultato, questo metodo blocca il thread corrente finché lo stato asincrono associato non è ready.  
  
 Per la specializzazione parziale `shared_future<Ty&>`, il valore archiviato è di fatto un riferimento all'oggetto passato al *provider asincrono* come valore restituito.  
  
 Poiché non esiste alcun valore archiviato per la specializzazione `shared_future<void>`, il metodo restituisce `void`.  
  
##  <a name="op_eq"></a>  shared_future::operator=  
 Trasferisce uno *stato asincrono associato* da un oggetto specificato.  
  
```
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```  
  
### <a name="parameters"></a>Parametri  
 `Right`  
 Oggetto `shared_future`.  
  
### <a name="return-value"></a>Valore restituito  
 `*this`  
  
### <a name="remarks"></a>Note  
 Per quanto riguarda il primo operatore, dopo l'operazione `Right` non ha più uno stato asincrono associato.  
  
 Per quanto riguarda il secondo metodo, `Right` mantiene lo stato asincrono associato.  
  
##  <a name="shared_future"></a>  Costruttore shared_future::shared_future  
 Costruisce un oggetto `shared_future`.  
  
```
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```  
  
### <a name="parameters"></a>Parametri  
 `Right`  
 Oggetto [future](../standard-library/future-class.md) o `shared_future`.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore crea un oggetto `shared_future` che non ha *stato asincrono associato*.  
  
 Il secondo e il terzo costruttore creano un oggetto `shared_future` e trasferiscono lo stato asincrono associato da `Right`. `Right` non ha un più uno stato asincrono associato.  
  
 Il quarto costruttore crea un oggetto `shared_future` con lo stesso stato asincrono associato di `Right`.  
  
##  <a name="valid"></a>shared_future:: Valid
 Specifica se l'oggetto ha uno *stato asincrono associato*.  
  
```
bool valid() noexcept;
```  
  
### <a name="return-value"></a>Valore restituito  
 `true` se l'oggetto ha uno stato asincrono associato; in caso contrario, `false`.  
  
##  <a name="wait"></a>shared_future:: Wait
 Blocca il thread corrente finché lo *stato asincrono associato* non è *ready*.  
  
```
void wait() const;
```  
  
### <a name="remarks"></a>Note  
 Uno stato asincrono associato è ready solo se il provider asincrono ha archiviato un valore restituito o un'eccezione.  
  
##  <a name="wait_for"></a>shared_future:: wait_for
 Blocca il thread corrente finché lo stato asincrono associato non è *ready* o finché non è trascorso un periodo di tempo specificato.  
  
```
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```  
  
### <a name="parameters"></a>Parametri  
 `Rel_time`  
 Oggetto [chrono::duration](../standard-library/duration-class.md) che specifica un intervallo di tempo massimo per il blocco del thread.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [future_status](../standard-library/future-enums.md#future_status) che indica il motivo della restituzione.  
  
### <a name="remarks"></a>Note  
 Uno stato asincrono associato è *ready* solo se il provider asincrono ha archiviato un valore restituito o un'eccezione.  
  
##  <a name="wait_until"></a>shared_future:: wait_until
 Blocca il thread corrente finché lo stato asincrono associato non è *ready* o fino a un determinato momento.  
  
```
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```  
  
### <a name="parameters"></a>Parametri  
 `Abs_time`  
 Oggetto [chrono::time_point](../standard-library/time-point-class.md) che specifica un momento dopo il quale il thread può essere sbloccato.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [future_status](../standard-library/future-enums.md#future_status) che indica il motivo della restituzione.  
  
### <a name="remarks"></a>Note  
 Uno stato asincrono associato è ready solo se il provider asincrono ha archiviato un valore restituito o un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento file di intestazione](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)



