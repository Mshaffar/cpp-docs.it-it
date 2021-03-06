---
title: Errore del compilatore C3390
ms.date: 11/04/2016
f1_keywords:
- C3390
helpviewer_keywords:
- C3390
ms.assetid: 84800a87-c8e6-45aa-82ae-02f816dc8d97
ms.openlocfilehash: 4c0544df55fc71ace697d7e0a53ba303706e1378
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201123"
---
# <a name="compiler-error-c3390"></a>Errore del compilatore C3390

'type_arg': argomento di tipo non valido per il parametro generico 'param' del 'generic_type' generico. Deve essere un tipo riferimento

L'istanza di un tipo generico è stata creata in modo non corretto.  Controllare la definizione del tipo.  Per altre informazioni, vedere [Generics](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Esempio

Nel primo esempio viene C# usato per creare un componente che contiene un tipo generico con determinati vincoli non supportati durante la creazione di tipi generici in C++/CLR. Per altre informazioni, vedere [Vincoli sui parametri di tipo](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters).

```csharp
// C3390.cs
// Compile by using: csc /target:library C3390.cs
// a C# program
public class GR<C, V, N>
where C : class
where V : struct
where N : new() {}
```

Quando il componente C3390. dll è disponibile, l'esempio seguente genera l'C3390.

```cpp
// C3390_b.cpp
// Compile by using: cl /clr C3390_b.cpp
#using <C3390.dll>
ref class R { R(int) {} };
value class V {};
ref struct N { N() {} };

int main () {
   GR<V, V, N^>^ gr2;   // C3390 first type must be a ref type
   GR<R^, V, N^>^ gr2b; // OK
}
```
