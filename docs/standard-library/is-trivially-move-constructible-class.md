---
title: Classe is_trivially_move_constructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_move_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b918809c0fabf7e0d65770dd12149d2f258189e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallymoveconstructible-class"></a>Classe is_trivially_move_constructible
Verifica se il tipo ha un costruttore di spostamento semplice.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class Ty>
struct is_trivially_move_constructible;
```  
  
#### <a name="parameters"></a>Parametri  
 `Ty`  
 Tipo su cui eseguire una query.  
  
## <a name="remarks"></a>Note  
 Un'istanza del predicato di tipo contiene true se il tipo `Ty` è una classe che ha un costruttore di spostamento semplice; in caso contrario, contiene false.  
  
 Un costruttore di spostamento per una classe `Ty` è piuttosto semplice se:  
  
 viene dichiarato in modo implicito  
  
 i tipi di parametro sono equivalenti a quelli di una dichiarazione implicita  
  
 la classe `Ty` non ha funzioni virtuali  
  
 la classe `Ty` non ha basi virtuali  
  
 la classe non ha alcun membro dati non statici volatili  
  
 tutte le basi dirette della classe `Ty` hanno costruttori di spostamento semplici  
  
 le classi di tutti i membri dati non statici del tipo di classe hanno costruttori di spostamento semplici  
  
 le classi di tutti i membri dati non statici di tipo matrice della classe hanno costruttori di spostamento semplici  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<type_traits>  
  
 **Spazio dei nomi:** std  
  
## <a name="see-also"></a>Vedere anche  
 [<type_traits>](../standard-library/type-traits.md)


