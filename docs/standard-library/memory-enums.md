---
title: Enumerazioni &lt;memory&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: d2f3cf1ec90c7caff5bb3a100d45d69a4a35e01a
ms.contentlocale: it-it
ms.lasthandoff: 04/19/2017

---
# <a name="ltmemorygt-enums"></a>Enumerazioni &lt;memory&gt;
||  
|-|  
|[pointer_safety](#pointer_safety)|  
  
##  <a name="pointer_safety"></a>  Enumerazione pointer_safety  
 Enumerazione dei valori possibili restituiti da `get_pointer_safety`.  
  
classe pointer_safety { relaxed, preferred, strict };  
  
### <a name="remarks"></a>Note  
 L'ambito di `enum` definisce i valori che possono essere restituiti da `get_pointer_safety``()`:  
  
 `relaxed` -- i puntatori non derivati in modo sicuro (ovviamente puntatori da dichiarare o oggetti allocati) sono considerati come quelli derivati in modo sicuro.  
  
 `preferred` -- come nella situazione precedente, ma i puntatori non derivati in modo sicuro non possono essere dereferenziati.  
  
 `strict` -- i puntatori non derivati in modo sicuro possono essere gestiti in modo diverso rispetto a quelli derivati in modo sicuro.  
  
## <a name="see-also"></a>Vedere anche  
 [\<memory>](../standard-library/memory.md)



