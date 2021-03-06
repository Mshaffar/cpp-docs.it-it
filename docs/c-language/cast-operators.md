---
title: Operatori di cast
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators
- type casts, operators
- operators [C++], cast
- type conversion, cast operators
ms.assetid: 43b90bbd-39ef-43e6-ae5d-e8a67a01de40
ms.openlocfilehash: e3d892a5aede4cd2d6a980b440875f0ac9837120
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312663"
---
# <a name="cast-operators"></a>Operatori di cast

Un cast di tipo fornisce un metodo per convertire esplicitamente il tipo di un oggetto in una situazione specifica.

## <a name="syntax"></a>Sintassi

*cast-expression*: *unary-expression*

*cast-expression* **(***Type-Name***)**      

Il compilatore considera *cast-expression* come di tipo *type-name* dopo un cast di tipo. I cast possono essere utilizzati per convertire gli oggetti di qualsiasi tipo scalare verso o da qualsiasi altro tipo scalare. I cast di tipo espliciti sono limitati dalle stesse regole che determinano gli effetti delle conversioni implicite descritte in [Conversioni di assegnazione](../c-language/assignment-conversions.md). I limiti aggiuntivi sui cast possono risultare dalle dimensioni effettive o dalla rappresentazione di tipi specifici. Vedere [Archiviazione dei tipi di base](../c-language/storage-of-basic-types.md) per informazioni sulle dimensioni effettive di tipi integrali. Per altre informazioni sui cast di tipo, vedere [Conversioni di cast di tipo](../c-language/type-cast-conversions.md).

## <a name="see-also"></a>Vedere anche

[Operatore cast: ()](../cpp/cast-operator-parens.md)
