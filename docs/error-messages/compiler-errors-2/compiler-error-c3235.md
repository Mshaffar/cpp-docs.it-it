---
title: Errore del compilatore C3235
ms.date: 11/04/2016
f1_keywords:
- C3235
helpviewer_keywords:
- C3235
ms.assetid: 0554d6c7-e1dc-4c99-8934-cbcf491c8203
ms.openlocfilehash: e284cf0d7742e60ceb5d381777ac68e9d0ea89be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759399"
---
# <a name="compiler-error-c3235"></a>Errore del compilatore C3235

'specialization': la specializzazione esplicita o parziale di una classe generica non è consentita

Le classi generiche non possono essere usate per le specializzazioni esplicite o parziali.

## <a name="example"></a>Esempio

L'esempio seguente genera l'errore C3235.

```cpp
// C3235.cpp
// compile with: /clr
generic<class T>
public ref class C {};

generic<>
public ref class C<int> {};   // C3235 Remove this specialization to resolve this error.
```
