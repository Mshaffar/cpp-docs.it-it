---
title: Classe is_nothrow_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_nothrow_assignable
dev_langs: C++
helpviewer_keywords: is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe32798dc98335dbada12e1914a77e89f0d78a25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="isnothrowassignable-class"></a>Classe is_nothrow_assignable
Verifica se un valore del tipo `From` può essere assegnato al tipo `To` e se l'assegnazione è nota come operazione che non genera eccezioni.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class To, class From>  
struct is_nothrow_assignable;
```  
  
#### <a name="parameters"></a>Parametri  
 Per  
 Il tipo di oggetto che riceve l'assegnazione.  
  
 Da  
 Il tipo di oggetto che fornisce il valore.  
  
## <a name="remarks"></a>Note  
 L'espressione `declval<To>() = declval<From>()` deve essere nel formato corretto e deve essere nota al compilatore come espressione che non genera eccezioni. `From` e `To` devono essere tipi completi, `void`, o matrici di valori associati sconosciuti.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<type_traits>  
  
 **Spazio dei nomi:** std  
  
## <a name="see-also"></a>Vedere anche  
 [<type_traits>](../standard-library/type-traits.md)


