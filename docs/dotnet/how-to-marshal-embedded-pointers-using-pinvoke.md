---
title: 'Procedura: Effettuare il marshalling di puntatori incorporati tramite PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- embedded pointers [C++]
- interop [C++], embedded pointers
- platform invoke [C++], embedded pointers
- marshaling [C++], embedded pointers
- data marshaling [C++], embedded pointers
ms.assetid: f12c1b9a-4f82-45f8-83c8-3fc9321dbb98
ms.openlocfilehash: 943a1a2784a37353157cd38da7ebdc9827006fe5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325208"
---
# <a name="how-to-marshal-embedded-pointers-using-pinvoke"></a>Procedura: Effettuare il marshalling di puntatori incorporati tramite PInvoke

Funzioni che sono implementate nella DLL non gestite possono essere chiamate da codice gestito tramite la funzionalità Platform Invoke (P/Invoke). Se il codice sorgente per la DLL non è disponibile, P/Invoke è l'unica opzione per l'interoperabilità. Tuttavia, a differenza di altri linguaggi .NET, Visual C++ offre un'alternativa al P/Invoke. Per altre informazioni, vedere [con funzionalità di interoperabilità C++ (PInvoke implicito)](../dotnet/using-cpp-interop-implicit-pinvoke.md) e [come: Effettuare il marshalling dei puntatori incorporati utilizzando l'interoperabilità C++](../dotnet/how-to-marshal-embedded-pointers-using-cpp-interop.md).

## <a name="example"></a>Esempio

Passaggio di strutture in codice nativo, è necessario che viene creata una struttura gestita equivalente in termini di layout dei dati per la struttura nativa. Tuttavia, le strutture che contengono puntatori richiedono una gestione speciale. Per ogni indicatore di misura incorporato nella struttura nativa, la versione gestita della struttura deve contenere un'istanza di <xref:System.IntPtr> tipo. Inoltre, della memoria per queste istanze devono essere allocate in modo esplicito, inizializzato e liberata usando il <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A>, <xref:System.Runtime.InteropServices.Marshal.StructureToPtr%2A>, e <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> metodi.

Il codice seguente è costituito da una funzione non gestita e un modulo gestito. Il modulo non gestito è una DLL che definisce una funzione che accetta una struttura denominata ListString che contiene un puntatore e una funzione denominata TakesListStruct. Il modulo gestito è un'applicazione della riga di comando che importa la funzione TakesListStruct e definisce una struttura denominata MListStruct equivale al ListStruct nativa ad eccezione del fatto che la doppia * è rappresentata con un <xref:System.IntPtr> istanza. Prima di chiamare TakesListStruct, la funzione principale alloca e inizializza la memoria a cui fa riferimento a questo campo.

```cpp
// TraditionalDll6.cpp
// compile with: /EHsc /LD
#include <stdio.h>
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct ListStruct {
   int count;
   double* item;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API void TakesListStruct(ListStruct);
}

void TakesListStruct(ListStruct list) {
   printf_s("[unmanaged] count = %d\n", list.count);
   for (int i=0; i<list.count; i++)
      printf_s("array[%d] = %f\n", i, list.item[i]);
}
```

```cpp
// EmbeddedPointerMarshalling.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MListStruct {
   int count;
   IntPtr item;
};

value struct TraditionalDLL {
    [DllImport("TraditionalDLL6.dll")]
   static public void TakesListStruct(MListStruct);
};

int main() {
   array<double>^ parray = gcnew array<double>(10);
   Console::WriteLine("[managed] count = {0}", parray->Length);

   Random^ r = gcnew Random();
   for (int i=0; i<parray->Length; i++) {
      parray[i] = r->NextDouble() * 100.0;
      Console::WriteLine("array[{0}] = {1}", i, parray[i]);
   }

   int size = Marshal::SizeOf(double::typeid);
   MListStruct list;
   list.count = parray->Length;
   list.item = Marshal::AllocCoTaskMem(size * parray->Length);

   for (int i=0; i<parray->Length; i++) {
      IntPtr t = IntPtr(list.item.ToInt32() + i * size);
      Marshal::StructureToPtr(parray[i], t, false);
   }

   TraditionalDLL::TakesListStruct( list );
   Marshal::FreeCoTaskMem(list.item);
}
```

Si noti che nessuna parte della DLL viene esposta al codice gestito usando le tradizionali #include (direttiva). In effetti, la DLL è accessibile in fase di esecuzione, quindi problemi con le funzioni importate con <xref:System.Runtime.InteropServices.DllImportAttribute> non viene rilevato in fase di compilazione.

## <a name="see-also"></a>Vedere anche

[Uso esplicito di PInvoke in C++ (attributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
