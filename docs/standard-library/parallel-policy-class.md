---
title: Classe parallel_policy
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 7bb2b095a50e664dfc585e0bd4aaa608a6ad8e95
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268963"
---
# <a name="parallelpolicy-class"></a>Classe parallel_policy

Utilizzato come un tipo univoco per risolvere l'ambiguità di overload di un algoritmo parallelo e indicare che l'esecuzione di un algoritmo parallelo possa essere eseguite in parallelo.

## <a name="syntax"></a>Sintassi

```cpp
class execution::parallel_policy;
```

## <a name="remarks"></a>Note

Durante l'esecuzione di un algoritmo parallelo con il `execution::parallel_policy` dei criteri, se si conclude la chiamata della funzione di accesso elemento tramite un'eccezione non rilevata, `terminate()` deve essere chiamato.
