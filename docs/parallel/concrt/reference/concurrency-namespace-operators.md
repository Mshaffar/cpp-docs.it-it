---
title: spazio dei nomi Concurrency operatori | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::operator!=
- concrt/concurrency:[operator&amp;&amp
- concrt/concurrency:[operator&amp;&amp
dev_langs:
- C++
ms.assetid: 8e373f23-fc8e-49f7-82e6-ba0c57b822f8
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 322c95da1774cb0b1d621a46c74125f435ebfbc4
ms.lasthandoff: 03/17/2017

---
# <a name="concurrency-namespace-operators"></a>spazio dei nomi Concurrency operatori
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&amp;&amp;](#operator_amp_amp)|[operator&gt;](#operator_gt)|  
|[operator&gt;=](#operator_gt_eq)|[operator&lt;](#operator_lt)|[operator&lt;=](#operator_lt_eq)|  
|[operator==](#operator_eq_eq)|[operator||](#operator_lor)|  
  
##  <a name="operator_lor"></a>operatore | | (Operatore)  
 Crea un'attività che verrà completata correttamente quando una delle attività fornite come argomenti verranno completate correttamente.  
  
```  
template<typename ReturnType>  
task<ReturnType> operator||(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>> operator||(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void> operator||(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>Parametri  
 `ReturnType`  
 Tipo dell'attività restituita.  
  
 `lhs`  
 La prima attività da combinare nell'attività risultante.  
  
 `rhs`  
 La seconda attività da combinare nell'attività risultante.  
  
### <a name="return-value"></a>Valore restituito  
 Attività che viene completata correttamente quando entrambe le attività di input sono state completate. Se le attività di input sono di tipo `T`, l'output di questa funzione sarà `task<std::vector<T>`. Se le attività di input sono di tipo `void`, anche l'attività di output sarà `task<void>`.  
  
### <a name="remarks"></a>Note  
 Se entrambe le attività vengono annullate o se vengono generate eccezioni, lo stato dell'attività restituita sarà impostato su annullato e una delle eventuali eccezioni verrà generata quando si chiama `get()` o `wait()` sull'attività in questione.  
  
##  <a name="operator_amp_amp"></a>operatore&amp; &amp; (operatore)  
 Crea un'attività che verrà completata correttamente quando entrambe le attività fornite come argomenti verranno completate.  
  
```  
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<ReturnType>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<ReturnType>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
template<typename ReturnType>  
task<std::vector<ReturnType>>  operator&&(
    const task<std::vector<ReturnType>>& lhs,  
    const task<std::vector<ReturnType>>& rhs);

 
inline task<void>  operator&&(
    const task<void>& lhs,  
    const task<void>& rhs);
```  
  
### <a name="parameters"></a>Parametri  
 `ReturnType`  
 Tipo dell'attività restituita.  
  
 `lhs`  
 La prima attività da combinare nell'attività risultante.  
  
 `rhs`  
 La seconda attività da combinare nell'attività risultante.  
  
### <a name="return-value"></a>Valore restituito  
 Attività che viene completata correttamente quando entrambe le attività di input sono state completate. Se le attività di input sono di tipo `T`, l'output di questa funzione sarà `task<std::vector<T>>`. Se le attività di input sono di tipo `void`, anche l'attività di output sarà `task<void>`.  
  
### <a name="remarks"></a>Note  
 Se una delle attività viene annullata o viene generata un'eccezione, l'attività restituita verrà completata in anticipo, nello stato annullato, e l'eccezione, se ne è presente una, verrà generata in caso di chiamata a `get()` o `wait()` sull'attività in questione.  
  
##  <a name="operator_eq_eq"></a>operatore Operator = =  
 Verifica se l'oggetto `concurrent_vector` sul lato sinistro dell'operatore è uguale all'oggetto `concurrent_vector` sul lato destro.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator== (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati degli elementi archiviati nel vettore simultaneo.  
  
 `A1`  
 Il tipo di allocatore del primo `concurrent_vector` oggetto.  
  
 `A2`  
 Il tipo di allocatore del secondo `concurrent_vector` oggetto.  
  
 `_A`  
 Oggetto di tipo `concurrent_vector`.  
  
 `_B`  
 Oggetto di tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il vettore simultaneo sul lato sinistro dell'operatore è uguale al vettore simultaneo sul lato destro dell'operatore; in caso contrario `false`.  
  
### <a name="remarks"></a>Note  
 Due vettori simultanei sono uguali se hanno lo stesso numero di elementi e i rispettivi elementi hanno gli stessi valori. In caso contrario, non sono uguali.  
  
 Questo metodo non è indipendente dalla concorrenza rispetto agli altri metodi che potrebbero modificare i vettori simultanei `_A` o `_B`.  
  
##  <a name="operator_neq"></a>operatore! = (operatore)  
 Verifica se l'oggetto `concurrent_vector` sul lato sinistro dell'operatore non è uguale all'oggetto `concurrent_vector` sul lato destro.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator!= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati degli elementi archiviati nel vettore simultaneo.  
  
 `A1`  
 Il tipo di allocatore del primo `concurrent_vector` oggetto.  
  
 `A2`  
 Il tipo di allocatore del secondo `concurrent_vector` oggetto.  
  
 `_A`  
 Oggetto di tipo `concurrent_vector`.  
  
 `_B`  
 Oggetto di tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se i vettori simultanei non sono uguali. `false` se i vettori simultanei sono uguali.  
  
### <a name="remarks"></a>Note  
 Due vettori simultanei sono uguali se hanno lo stesso numero di elementi e i rispettivi elementi hanno gli stessi valori. In caso contrario, non sono uguali.  
  
 Questo metodo non è indipendente dalla concorrenza rispetto agli altri metodi che potrebbero modificare i vettori simultanei `_A` o `_B`.  
  
##  <a name="operator_lt"></a>operatore&lt; (operatore)  
 Verifica se l'oggetto `concurrent_vector` sul lato sinistro dell'operatore è minore dell'oggetto `concurrent_vector` sul lato destro.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati degli elementi archiviati nel vettore simultaneo.  
  
 `A1`  
 Il tipo di allocatore del primo `concurrent_vector` oggetto.  
  
 `A2`  
 Il tipo di allocatore del secondo `concurrent_vector` oggetto.  
  
 `_A`  
 Oggetto di tipo `concurrent_vector`.  
  
 `_B`  
 Oggetto di tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il vettore simultaneo sul lato sinistro dell'operatore è minore di vettore simultaneo sul lato destro dell'operatore; in caso contrario `false`.  
  
### <a name="remarks"></a>Note  
 Il comportamento di questo operatore è identico all'operatore equivalente per la `vector` classe il `std` dello spazio dei nomi.  
  
 Questo metodo non è indipendente dalla concorrenza rispetto agli altri metodi che potrebbero modificare i vettori simultanei `_A` o `_B`.  
  
##  <a name="operator_lt_eq"></a>operatore&lt;= (operatore)  
 Verifica se l'oggetto `concurrent_vector` sul lato sinistro dell'operatore è minore o uguale all'oggetto `concurrent_vector` sul lato destro.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator<= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati degli elementi archiviati nel vettore simultaneo.  
  
 `A1`  
 Il tipo di allocatore del primo `concurrent_vector` oggetto.  
  
 `A2`  
 Il tipo di allocatore del secondo `concurrent_vector` oggetto.  
  
 `_A`  
 Oggetto di tipo `concurrent_vector`.  
  
 `_B`  
 Oggetto di tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il vettore simultaneo sul lato sinistro dell'operatore è minore o uguale al vettore simultaneo sul lato destro dell'operatore; in caso contrario `false`.  
  
### <a name="remarks"></a>Note  
 Il comportamento di questo operatore è identico all'operatore equivalente per la `vector` classe il `std` dello spazio dei nomi.  
  
 Questo metodo non è indipendente dalla concorrenza rispetto agli altri metodi che potrebbero modificare i vettori simultanei `_A` o `_B`.  
  
##  <a name="operator_gt"></a>operatore&gt; (operatore)  
 Verifica se l'oggetto `concurrent_vector` sul lato sinistro dell'operatore è maggiore dell'oggetto `concurrent_vector` sul lato destro.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>(
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati degli elementi archiviati nel vettore simultaneo.  
  
 `A1`  
 Il tipo di allocatore del primo `concurrent_vector` oggetto.  
  
 `A2`  
 Il tipo di allocatore del secondo `concurrent_vector` oggetto.  
  
 `_A`  
 Oggetto di tipo `concurrent_vector`.  
  
 `_B`  
 Oggetto di tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valore restituito  
 `true` se il vettore simultaneo sul lato sinistro dell'operatore è maggiore rispetto a quello sul lato destro dell'operatore; in caso contrario `false`.  
  
### <a name="remarks"></a>Note  
 Il comportamento di questo operatore è identico all'operatore equivalente per la `vector` classe il `std` dello spazio dei nomi.  
  
 Questo metodo non è indipendente dalla concorrenza rispetto agli altri metodi che potrebbero modificare i vettori simultanei `_A` o `_B`.  
  
##  <a name="operator_gt_eq"></a>operatore&gt;= (operatore)  
 Verifica se l'oggetto `concurrent_vector` sul lato sinistro dell'operatore è maggiore o uguale all'oggetto `concurrent_vector` sul lato destro.  
  
```  
template<typename T, class A1, class A2>  
inline bool operator>= (
    const concurrent_vector<T, A1>& _A,  
    const concurrent_vector<T, A2>& _B);
```  
  
### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati degli elementi archiviati nel vettore simultaneo.  
  
 `A1`  
 Il tipo di allocatore del primo `concurrent_vector` oggetto.  
  
 `A2`  
 Il tipo di allocatore del secondo `concurrent_vector` oggetto.  
  
 `_A`  
 Oggetto di tipo `concurrent_vector`.  
  
 `_B`  
 Oggetto di tipo `concurrent_vector`.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il vettore simultaneo sul lato sinistro dell'operatore è maggiore o uguale al vettore simultaneo sul lato destro dell'operatore; in caso contrario `false`.  
  
### <a name="remarks"></a>Note  
 Il comportamento di questo operatore è identico all'operatore equivalente per la `vector` classe il `std` dello spazio dei nomi.  
  
 Questo metodo non è indipendente dalla concorrenza rispetto agli altri metodi che potrebbero modificare i vettori simultanei `_A` o `_B`.  
  
## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi concurrency](concurrency-namespace.md)
