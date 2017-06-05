---
title: Struttura system_clock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
dev_langs:
- C++
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
caps.latest.revision: 14
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
ms.openlocfilehash: 053b2930d25bb7b1ec073764801530860511ac1b
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="systemclock-structure"></a>Struttura system_clock
Rappresenta un *tipo di clock* basato sull'orologio in tempo reale del sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
struct system_clock;  
```  
  
## <a name="remarks"></a>Note  
 Un *tipo di clock* viene usato per ottenere l'ora corrente come ora UTC. Il tipo incorpora la creazione di un'istanza di [duration](../standard-library/duration-class.md) e il modello di classe [time_point](../standard-library/time-point-class.md) e definisce una funzione membro statica `now()` che restituisce l'ora.  
  
 Un clock è *monotonico* se il valore restituito da una prima chiamata a `now()` è sempre minore o uguale al valore restituito da una chiamata successiva a `now()`.  
  
 Un clock è *costante* se è *monotonico* e se il tempo tra i cicli macchina è costante.  
  
 In questa implementazione, un `system_clock` è sinonimo di un `high_resolution_clock`.  
  
## <a name="members"></a>Membri  
  
### <a name="public-typedefs"></a>Typedef pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|`system_clock::duration`|Sinonimo di `duration<rep, period>`.|  
|`system_clock::period`|Un sinonimo del tipo che viene usato per rappresentare il periodo dei cicli macchina nella creazione di un'istanza contenuta di `duration`.|  
|`system_clock::rep`|Un sinonimo del tipo che viene usato per rappresentare il numero di cicli macchina nella creazione di un'istanza contenuta di `duration`.|  
|`system_clock::time_point`|Un sinonimo per `time_point<Clock, duration>`, dove `Clock` è un sinonimo per il tipo di clock stesso o un altro tipo di clock che si basa su epoch stesso e ha lo stesso tipo `duration` nidificato.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[from_time_t](#from_time_t)|Statico. Restituisce un oggetto `time_point` che più si avvicina un'ora specificata.|  
|[a questo punto](#now)|Statico. Restituisce l'ora corrente.|  
|[to_time_t](#to_time_t)|Statico. Restituisce un oggetto `time_t` che più si avvicina un oggetto `time_point` specificato.|  
  
### <a name="public-constants"></a>Costanti pubbliche  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Costante system_clock::is_monotonic](#is_monotonic_constant)|Specifica se il tipo di clock è monotonico.|  
|[Costante system_clock::is_steady](#is_steady_constant)|Specifica se il tipo di clock è costante.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<chrono >  
  
 **Spazio dei nomi:**std::chrono  
  
##  <a name="from_time_t"></a>system_clock:: from_time_t
 Metodo statico che restituisce un oggetto [time_point](../standard-library/time-point-class.md) che più si avvicina all'ora rappresentata da `Tm`.  
  
```  
static time_point from_time_t(time_t Tm) noexcept;  
```  
  
### <a name="parameters"></a>Parametri  
 `Tm`  
 Oggetto [time_t](../c-runtime-library/standard-types.md).  
  
##  <a name="is_monotonic_constant"></a>  Costante system_clock::is_monotonic  
 Valore statico che specifica se il tipo di clock è monotonico.  
  
```  
static const bool is_monotonic = false;  
```  
  
### <a name="return-value"></a>Valore restituito  
 In questa implementazione, `system_clock::is_monotonic` restituisce sempre `false`.  
  
### <a name="remarks"></a>Note  
 Un clock è *monotonico* se il valore restituito da una prima chiamata a `now()` è sempre minore o uguale al valore restituito da una chiamata successiva a `now()`.  
  
##  <a name="is_steady_constant"></a>  Costante system_clock::is_steady  
 Valore statico che specifica se il tipo di clock è *costante*.  
  
```  
static const bool is_steady = false;  
```  
  
### <a name="return-value"></a>Valore restituito  
 In questa implementazione, `system_clock::is_steady` restituisce sempre `false`.  
  
### <a name="remarks"></a>Note  
 Un clock è *costante* se è [monotonico](#is_monotonic_constant) e se il tempo tra i cicli macchina è costante.  
  
##  <a name="now"></a>system_clock:: Now
 Metodo statico che restituisce l'ora corrente.  
  
```  
static time_point now() noexcept;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto [time_point](../standard-library/time-point-class.md) che rappresenta l'ora corrente.  
  
##  <a name="to_time_t"></a>system_clock:: to_time_t
 Metodo statico che restituisce un oggetto [time_t](../c-runtime-library/standard-types.md) che più si avvicina all'ora rappresentata da `Time`.  
  
```  
static time_t to_time_t(const time_point& Time) noexcept;  
```  
  
### <a name="parameters"></a>Parametri  
 `Time`  
 Oggetto [time_point](../standard-library/time-point-class.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Header Files Reference](../standard-library/cpp-standard-library-header-files.md)  (Riferimento file di intestazione)  
 [\<chrono>](../standard-library/chrono.md)   
 [steady_clock struct](../standard-library/steady-clock-struct.md)
