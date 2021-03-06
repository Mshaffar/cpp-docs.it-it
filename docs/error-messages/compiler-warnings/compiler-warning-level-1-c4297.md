---
title: Avviso del compilatore (livello 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 31deba2f421b461ba56d13810b5064b353a0e602
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175675"
---
# <a name="compiler-warning-level-1-c4297"></a>Avviso del compilatore (livello 1) C4297

'function': la funzione genera un'eccezione benché ciò non fosse previsto

Una dichiarazione di funzione contiene un identificatore di `noexcept` (possibilmente implicito), un identificatore di eccezione `throw` vuota o un attributo [__declspec (nothrow)](../../cpp/nothrow-cpp.md) e la definizione contiene una o più istruzioni [throw](../../cpp/try-throw-and-catch-statements-cpp.md) . Per risolvere l'errore C4297, non tentare di generare eccezioni in funzioni dichiarate `__declspec(nothrow)`, `noexcept(true)` o `throw()`. In alternativa, rimuovere la specifica `noexcept`, `throw()` o `__declspec(nothrow)`.

Per impostazione predefinita, il compilatore genera identificatori `noexcept(true)` impliciti per le funzioni di deallocatori e distruttori definiti dall'utente e le speciali funzioni membro generate dal compilatore. Ciò è conforme allo standard ISO C++11. Per evitare la generazione di identificatori noexcept impliciti e ripristinare il comportamento non standard di Visual Studio 2013, usare l'opzione **/Zc: implicitNoexcept-** Compiler. Per altre informazioni, vedere [/Zc: implicitNoexcept (identificatori di eccezioni implicite)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Per altre informazioni sulle specifiche di eccezione, vedere [specifiche di eccezione (throw)](../../cpp/exception-specifications-throw-cpp.md). Vedere anche [/eh (modello di gestione delle eccezioni)](../../build/reference/eh-exception-handling-model.md) per informazioni su come modificare il comportamento di gestione delle eccezioni in fase di compilazione.

Questo avviso viene generato anche per le funzioni di __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) contrassegnate come extern "C", C++ anche se sono funzioni.

L'esempio seguente genera l'errore C4297:

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```
