---
title: Classe discard_block_engine
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: eb00945084affb2be9299953e5ca9352c56d3b32
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688097"
---
# <a name="discard_block_engine-class"></a>Classe discard_block_engine

Genera una sequenza casuale, eliminando i valori restituiti dal motore di base corrispondente.

## <a name="syntax"></a>Sintassi

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parametri

@No__t_1 del *motore*
Tipo del motore di base.

@No__t_1 *P*
**Dimensioni del blocco**. Numero di valori in ogni blocco.

*R*\
**Blocco usato**. Numero di valori usati in ogni blocco. Il resto viene scartato (`P`  -  `R`). **Precondizione**:`0 < R ≤ P`

## <a name="members"></a>Members

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Per altre informazioni sui membri del motore, vedere [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Note

Questo modello di classe descrive un adattatore del motore che produce valori ignorando alcuni dei valori restituiti dal motore di base.

## <a name="requirements"></a>Requisiti

**Intestazione:** \<random>

**Spazio dei nomi:** std

## <a name="see-also"></a>Vedere anche

[\<random>](../standard-library/random.md)
