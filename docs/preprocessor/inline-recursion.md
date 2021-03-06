---
title: Pragma inline_recursion
ms.date: 08/29/2019
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
ms.openlocfilehash: 0169e06e8e47f7b0a7b3f73e809ddc988bcf1e95
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220960"
---
# <a name="inline_recursion-pragma"></a>Pragma inline_recursion

Controlla l'espansione inline delle chiamate di funzione dirette o ricorsive reciproche.

## <a name="syntax"></a>Sintassi

> **#pragma inline_recursion (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Note

Usare questo pragma per controllare funzioni contrassegnate come [inline](../cpp/inline-functions-cpp.md) e [__inline](../cpp/inline-functions-cpp.md) o funzioni che il compilatore espande automaticamente in base `/Ob2` all'opzione. L'uso di questo pragma richiede un'impostazione dell'opzione del compilatore [/ob](../build/reference/ob-inline-function-expansion.md) 1 o 2. Lo stato predefinito per **inline_recursion** è off. Questo pragma viene applicato alla prima chiamata di funzione dopo che il pragma è stato individuato e non influisce sulla definizione della funzione.

Il pragma **inline_recursion** controlla il modo in cui le funzioni ricorsive vengono espanse. Se **inline_recursion** è off e se una funzione inline chiama se stessa, direttamente o indirettamente, la funzione viene espansa solo una volta. Se **inline_recursion** è impostata su on, la funzione viene espansa più volte fino a raggiungere il valore impostato con il pragma [inline_depth](../preprocessor/inline-depth.md) , il valore predefinito per le funzioni ricorsive `inline_depth` definite dal pragma o un limite di capacità.

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[inline_depth](../preprocessor/inline-depth.md)\
[/Ob (espansione funzioni inline)](../build/reference/ob-inline-function-expansion.md)
