---
title: Operatori &lt;allocators&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
dev_langs:
- C++
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 11
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: c6b19eb0c4f8d63ce288ce47a759e949714daf5e
ms.contentlocale: it-it
ms.lasthandoff: 10/03/2017

---
# <a name="ltallocatorsgt-operators"></a>Operatori &lt;allocators&gt;
|||  
|-|-|  
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 Verifica la disuguaglianza tra gli oggetti allocatore di una classe specificata.  
  
```
template <class Type, class Sync>  
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`left`|Uno degli oggetti allocatore di cui verificare la disuguaglianza.|  
|`right`|Uno degli oggetti allocatore di cui verificare la disuguaglianza.|  
  
### <a name="return-value"></a>Valore restituito  
 **true** se gli oggetti allocatore non sono uguali; **false** se gli oggetti allocatore sono uguali.  
  
### <a name="remarks"></a>Note  
 L'operatore di modello restituisce `!(left == right)`.  
  
##  <a name="op_eq_eq"></a>  operator==  
 Verifica l'uguaglianza tra gli oggetti allocatore di una classe specificata.  
  
```
template <class Type, class Sync>  
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`left`|Uno degli oggetti allocatore di cui verificare l'uguaglianza.|  
|`right`|Uno degli oggetti allocatore di cui verificare l'uguaglianza.|  
  
### <a name="return-value"></a>Valore restituito  
 **true** se gli oggetti allocatore sono uguali; **false** se gli oggetti allocatore non sono uguali.  
  
### <a name="remarks"></a>Note  
 Questo operatore di modello restituisce `left.equals(right)`.  
  
## <a name="see-also"></a>Vedere anche  
 [\<allocators>](../standard-library/allocators-header.md)



