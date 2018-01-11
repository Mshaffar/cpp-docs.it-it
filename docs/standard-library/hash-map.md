---
title: '&lt;hash_map&gt; | Microsoft Docs'
ms.custom: 
ms.date: 09/18/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <hash_map>
- std::<hash_map>
dev_langs: C++
helpviewer_keywords: hash_map header
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a996142e128f4113fb9d1057cd061155dae251f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;
> [!NOTE]
>  Questa intestazione è obsoleta. L'alternativa è [ \<unordered_map >](unordered-map.md).  
  
 Definisce le classi del modello del contenitore hash_map e hash_multimap e i relativi modelli di supporto.  
 
  
## <a name="syntax"></a>Sintassi  
  
```  
#include <hash_map>  
  
```  
  
### <a name="operators"></a>Operatori  
  
|Versione hash_map|Versione hash_multimap|Descrizione|  
|-----------------------|----------------------------|-----------------|  
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator!=(hash_multimap)](hash-map-operators.md#op_neq_mm)|Verifica se l'oggetto hash_map o hash_multimap a sinistra dell'operatore non è uguale all'oggetto hash_map o hash_multimap a destra.|  
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operatore = = (hash_multimap)] ((hash-mappa-operators.md #op_eq_eq_mm)|Verifica se l'oggetto hash_map o hash_multimap a sinistra dell'operatore è uguale all'oggetto hash_map o hash_multimap a destra.|  
  
### <a name="specialized-template-functions"></a>Funzioni di modello specializzate  
  
|Versione hash_map|Versione hash_multimap|Descrizione|  
|-----------------------|----------------------------|-----------------|  
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Scambia gli elementi di due oggetti hash_map o hash_multimap.|  
  
### <a name="classes"></a>Classi  
  
|||  
|-|-|  
|[Classe hash_compare](hash-compare-class.md)|Descrive un oggetto che può essere usato da uno qualsiasi dei contenitori associativi hash, hash_map, hash_multimap, hash_set o hash_multiset, come oggetto del parametro **Traits** predefinito per l'ordinamento e l'hashing degli elementi contenuti.|  
|[Classe value_compare](value-compare-class.md)|Fornisce un oggetto funzione in grado di confrontare gli elementi di un oggetto hash_map comparando i valori delle chiavi per determinarne l'ordine relativo nell'oggetto hash_map.|  
|[Classe hash_map](hash-map-class.md)|Usata per archiviare e recuperare rapidamente i dati da una raccolta in cui ogni elemento è una coppia che ha una chiave di ordinamento con valore univoco e un valore di dati associato.|  
|[Classe hash_multimap](hash-multimap-class.md)|Usata per archiviare e recuperare rapidamente i dati da una raccolta in cui ogni elemento è una coppia con una chiave di ordinamento il cui valore non deve essere univoco e un valore di dati associato.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<hash_map>  
  
 **Spazio dei nomi:** stdext  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento file di intestazione](cpp-standard-library-header-files.md)   
 [Thread Safety in the C++ Standard Library](thread-safety-in-the-cpp-standard-library.md)  (Sicurezza dei thread nella libreria standard C++)  
 [Riferimento per la libreria standard C++](cpp-standard-library-reference.md)


