---
title: Operatori di spazio dei nomi Concurrency (AMP) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: 
dev_langs:
- C++
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 22ba62ab8b3b4f9d14953dbab3edd8228ea85193
ms.openlocfilehash: 676f3e836082dc3286a45f8d59db83c969964058
ms.lasthandoff: 02/24/2017

---
# <a name="concurrency-namespace-operators-amp"></a>Operatori di spazio dei nomi Concurrency (AMP)
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator%](#operator_mod)|[operator*](#operator_star)|  
|[operator+](#operator_add)|[operator-](#operator-)|[operator/](#operator_div)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="operator_eq_eq"></a>  operator==   
 Determina se gli argomenti specificati sono uguali.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parametri  
 `_Rank`  
 La classificazione degli argomenti di tupla.  
  
 `_Lhs`  
 Una delle tuple da confrontare.  
  
 `_Rhs`  
 Una delle tuple da confrontare.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se le tuple sono uguali. in caso contrario, `false`.  
  
##  <a name="operator_neq"></a>  operator!=   
 Determina se gli argomenti specificati non sono uguali.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```  
  
### <a name="parameters"></a>Parametri  
 `_Rank`  
 La classificazione degli argomenti di tupla.  
  
 `_Lhs`  
 Una delle tuple da confrontare.  
  
 `_Rhs`  
 Una delle tuple da confrontare.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se le tuple non sono uguali. in caso contrario, `false`.  
  
##  <a name="operator_add"></a>  operator+   

 Calcola la somma component-wise di argomenti specificati.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametri  
 `_Rank`  
 La classificazione degli argomenti di tupla.  
  
 `_Lhs`  
 Uno degli argomenti da aggiungere.  
  
 `_Rhs`  
 Uno degli argomenti da aggiungere.  
  
### <a name="return-value"></a>Valore restituito  
 La somma component-wise di argomenti specificati.  
  
##  <a name="operator-"></a>  operator-   

 Calcola la differenza component-wise tra gli argomenti specificati.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametri  
 `_Rank`  
 La classificazione degli argomenti di tupla.  
  
 `_Lhs`  
 L'argomento da sottrarre.  
  
 `_Rhs`  
 L'argomento da sottrarre.  
  
### <a name="return-value"></a>Valore restituito  
 La differenza component-wise tra gli argomenti specificati.  
  
##  <a name="operator_star"></a>  operator*   

 Calcola il prodotto component-wise di argomenti specificati.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>Parametri  
 `_Rank`  
 La classificazione degli argomenti di tupla.  
  
 `_Lhs`  
 Una delle tuple da moltiplicare.  
  
 `_Rhs`  
 Una delle tuple da moltiplicare.  
  
### <a name="return-value"></a>Valore restituito  
 Il prodotto component-wise di argomenti specificati.  
  

##  <a name="operator_div"></a>  operator/   
 Calcola il quoziente component-wise tra gli argomenti specificati.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametri  
 `_Rank`  
 La classificazione degli argomenti di tupla.  
  
 `_Lhs`  
 La tupla da dividere.  
  
 `_Rhs`  
 La tupla per cui dividere.  
  
### <a name="return-value"></a>Valore restituito  
 Il quoziente component-wise di argomenti specificati.  
  
##  <a name="operator_mod"></a>  operator%   

 Calcola il modulo del primo argomento specificato dal secondo argomento specificato.  
  
```  
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,  
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

 
template <
    int _Rank,  
    template <int> class _Tuple_type  
>  
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,  
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>Parametri  
 `_Rank`  
 La classificazione degli argomenti di tupla.  
  
 `_Lhs`  
 La tupla da cui il modulo viene calcolata.  
  
 `_Rhs`  
 La tupla di modulo da.  
  
### <a name="return-value"></a>Valore restituito  
 Il risultato del modulo della primo argomento specificato, il secondo argomento specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Concorrenza Namespace](concurrency-namespace-cpp-amp.md)
