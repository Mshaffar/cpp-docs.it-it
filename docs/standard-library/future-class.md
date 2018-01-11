---
title: Classe future | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
dev_langs: C++
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: ce91279c4504e9373a151286167f36d3b3439cbc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="future-class"></a>Classe future
Descrive un *oggetto restituito asincrono*.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class Ty>
class future;
```  
  
## <a name="remarks"></a>Note  
 Ogni *provider asincrono* standard restituisce un oggetto il cui tipo è una creazione di un'istanza del modello. Un oggetto `future` fornisce l'unico accesso al provider asincrono a cui è associato. Se sono necessari più oggetti restituiti asincroni associati allo stesso provider asincrono, copiare l'oggetto `future` in un oggetto [shared_future](../standard-library/shared-future-class.md).  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[future](#future)|Costruisce un oggetto `future`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[get](#get)|Recupera il risultato archiviato nello stato asincrono associato.|  
|[Condividi](#share)|Converte l'oggetto in `shared_future`.|  
|[valido](#valid)|Specifica se l'oggetto non è vuoto.|  
|[attesa](#wait)|Blocca il thread corrente finché lo stato asincrono associato non è ready.|  
|[wait_for](#wait_for)|Blocca finché lo stato asincrono associato non è ready o finché non trascorre il periodo di tempo specificato.|  
|[wait_until](#wait_until)|Blocca finché lo stato asincrono associato non è ready o fino al momento specificato.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[future::operator=](#op_eq)|Trasferisce lo stato asincrono associato da un oggetto specificato.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<futura >  
  
 **Spazio dei nomi:** std  
  
##  Costruttore <a name="future"></a>  future::future  
 Costruisce un oggetto `future`.  
  
```
future() noexcept;
future(future&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parametri  
 `Other`  
 Oggetto `future`.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore crea un oggetto `future` che non ha uno stato asincrono associato.  
  
 Il secondo costruttore crea un oggetto `future` e trasferisce lo stato asincrono associato da `Other`. `Other` non ha un più uno stato asincrono associato.  
  
##  <a name="get"></a>  future::get  
 Recupera il risultato archiviato nello stato asincrono associato.  
  
```
Ty get();
```  
  
### <a name="return-value"></a>Valore restituito  
 Se il risultato è un'eccezione, il metodo la genera nuovamente. In caso contrario, viene restituito il risultato.  
  
### <a name="remarks"></a>Note  
 Prima di recuperare il risultato, questo metodo blocca il thread corrente finché lo stato asincrono associato non è ready.  
  
 Per la specializzazione parziale `future<Ty&>`, il valore archiviato è di fatto un riferimento all'oggetto passato al provider asincrono come valore restituito.  
  
 Poiché non esiste alcun valore archiviato per la specializzazione `future<void>`, il metodo restituisce `void`.  
  
 In altre specializzazioni il metodo sposta il relativo valore restituito dal valore archiviato. Pertanto, chiamare questo metodo solo una volta.  
  
##  <a name="op_eq"></a>  future::operator=  
 Trasferisce uno stato asincrono associato da un oggetto specificato.  
  
```
future& operator=(future&& Right) noexcept;
```  
  
### <a name="parameters"></a>Parametri  
 `Right`  
 Oggetto `future`.  
  
### <a name="return-value"></a>Valore restituito  
 `*this`  
  
### <a name="remarks"></a>Note  
 Dopo il trasferimento, `Right` non ha più uno stato asincrono associato.  
  
##  <a name="share"></a>  future::share  
 Converte l'oggetto in un oggetto [shared_future](../standard-library/shared-future-class.md).  
  
```
shared_future<Ty> share();
```  
  
### <a name="return-value"></a>Valore restituito  
 `shared_future(move(*this))`  
  
##  <a name="valid"></a>  future::valid  
 Specifica se l'oggetto ha uno stato asincrono associato.  
  
```
bool valid() noexcept;
```  
  
### <a name="return-value"></a>Valore restituito  
 `true` se l'oggetto ha uno stato asincrono associato; in caso contrario, `false`.  
  
##  <a name="wait"></a>  future::wait  
 Blocca il thread corrente finché lo stato asincrono associato non è *ready*.  
  
```cpp  
void wait() const;
```  
  
### <a name="remarks"></a>Note  
 Lo stato asincrono associato è *ready* solo se il relativo provider asincrono ha archiviato un valore restituito o un'eccezione.  
  
##  <a name="wait_for"></a>  future::wait_for  
 Blocca il thread corrente finché lo stato asincrono associato non è *ready* o finché non trascorre un determinato intervallo di tempo.  
  
```
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```  
  
### <a name="parameters"></a>Parametri  
 `Rel_time`  
 Oggetto [chrono::duration](../standard-library/duration-class.md) che specifica un intervallo di tempo massimo per il blocco del thread.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [future_status](../standard-library/future-enums.md#future_status) che indica il motivo della restituzione.  
  
### <a name="remarks"></a>Note  
 Lo stato asincrono associato è ready solo se il relativo provider asincrono ha archiviato un valore restituito o un'eccezione.  
  
##  <a name="wait_until"></a>  future::wait_until  
 Blocca il thread corrente finché lo stato asincrono associato non è *ready* o fino a un determinato momento.  
  
```cpp  
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```  
  
### <a name="parameters"></a>Parametri  
 `Abs_time`  
 Oggetto [chrono::time_point](../standard-library/time-point-class.md) che specifica un momento dopo il quale il thread può essere sbloccato.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [future_status](../standard-library/future-enums.md#future_status) che indica il motivo della restituzione.  
  
### <a name="remarks"></a>Note  
 Lo stato asincrono associato è *ready* solo se il relativo provider asincrono ha archiviato un valore restituito o un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento file di intestazione](../standard-library/cpp-standard-library-header-files.md)   
 [\<future>](../standard-library/future.md)


