---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: 6bb2ca0cc14bcc4a9b9df9877902de9181e0a768
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77258146"
---
# <a name="lthash_mapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Questa intestazione è obsoleta. L'alternativa è [\<unordered_map >](unordered-map.md).

Definisce i modelli di classe del contenitore hash_map e hash_multimap e i relativi modelli di supporto.

## <a name="syntax"></a>Sintassi

```cpp
#include <hash_map>
```

### <a name="operators"></a>Operatori

|Versione hash_map|Versione hash_multimap|Descrizione|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operatore! = (hash_multimap)](hash-map-operators.md#op_neq_mm)|Verifica se l'oggetto hash_map o hash_multimap a sinistra dell'operatore non è uguale all'oggetto hash_map o hash_multimap a destra.|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Verifica se l'oggetto hash_map o hash_multimap a sinistra dell'operatore è uguale all'oggetto hash_map o hash_multimap a destra.|

### <a name="specialized-template-functions"></a>Funzioni di modello specializzate

|Versione hash_map|Versione hash_multimap|Descrizione|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Scambia gli elementi di due oggetti hash_map o hash_multimap.|

### <a name="classes"></a>Classi

|Classe|Descrizione|
|-|-|
|[Classe hash_compare](hash-compare-class.md)|Descrive un oggetto che può essere usato da uno qualsiasi dei contenitori associativi hash, ovvero hash_map, hash_multimap, hash_set o hash_multiset, come oggetto parametro di `Traits` predefinito per ordinare ed eseguire l'hashing degli elementi in essi contenuti.|
|[Classe value_compare](value-compare-class.md)|Fornisce un oggetto funzione in grado di confrontare gli elementi di un oggetto hash_map comparando i valori delle chiavi per determinarne l'ordine relativo nell'oggetto hash_map.|
|[Classe hash_map](hash-map-class.md)|Usata per archiviare e recuperare rapidamente i dati da una raccolta in cui ogni elemento è una coppia che ha una chiave di ordinamento con valore univoco e un valore di dati associato.|
|[Classe hash_multimap](hash-multimap-class.md)|Usata per archiviare e recuperare rapidamente i dati da una raccolta in cui ogni elemento è una coppia con una chiave di ordinamento il cui valore non deve essere univoco e un valore di dati associato.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<hash_map >

**Spazio dei nomi:** stdext

## <a name="see-also"></a>Vedere anche

[Header Files Reference](cpp-standard-library-header-files.md)\ (Riferimento file di intestazione)
[Thread Safety in the C++ Standard Library](thread-safety-in-the-cpp-standard-library.md)\ (Sicurezza dei thread nella libreria standard C++)
[Riferimento per la libreria standard C++](cpp-standard-library-reference.md)
