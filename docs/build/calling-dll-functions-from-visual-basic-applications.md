---
title: Chiamata di funzioni DLL da applicazioni Visual Basic
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
ms.openlocfilehash: 23b5692e28b9ea5b70c492e2564b8bf5385b1815
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221192"
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Chiamata di funzioni DLL da applicazioni Visual Basic

Per Visual Basic applicazioni (o applicazioni in altri linguaggi, ad esempio Pascal o FORTRAN) per chiamare funzioni in una DLL C/C++, le funzioni devono essere esportate utilizzando la convenzione di chiamata corretta senza alcuna decorazione del nome eseguita dal compilatore

`__stdcall`Crea la convenzione di chiamata corretta per la funzione (la funzione chiamata pulisce lo stack e i parametri vengono passati da destra a sinistra), ma decora il nome della funzione in modo diverso. Pertanto, quando **__declspec (dllexport)** viene utilizzato in una funzione esportata in una dll, viene esportato il nome decorato.

La `__stdcall` decorazione del nome prefissa il nome del simbolo con un carattere **\_** di sottolineatura () e aggiunge il simbolo con**\@** un carattere di chiocciola () seguito dal numero di byte nell'elenco di argomenti (lo spazio dello stack richiesto). Di conseguenza, la funzione viene dichiarata come:

```C
int __stdcall func (int a, double b)
```

è decorato `_func@12` come nell'output.

La convenzione di chiamata C`__cdecl`() decora il nome come `_func`.

Per ottenere il nome decorato, usare [/Map](reference/map-generate-mapfile.md). L'uso di **__declspec (dllexport)** esegue le operazioni seguenti:

- Se la funzione viene esportata con la convenzione di`__cdecl`chiamata C (), il carattere di sottolineatura ( **\_** ) viene ritagliato quando il nome viene esportato.

- Se la funzione esportata non usa la convenzione di chiamata C (ad esempio `__stdcall`,), esporta il nome decorato.

Poiché non è possibile eseguire l'override del punto in cui viene eseguita la pulizia dello `__stdcall`stack, è necessario utilizzare. Per dedecorare i nomi `__stdcall`con, è necessario specificarli usando gli alias nella sezione EXPORTS del file def. Come illustrato di seguito per la seguente dichiarazione di funzione:

```C
int  __stdcall MyFunc (int a, double b);
void __stdcall InitCode (void);
```

Nel. File DEF:

```
EXPORTS
   MYFUNC=_MyFunc@12
   INITCODE=_InitCode@0
```

Per chiamare le dll da programmi scritti in Visual Basic, è necessario usare la tecnica alias illustrata in questo argomento nel file def. Se l'alias viene eseguito nel programma Visual Basic, non è necessario usare l'aliasing nel file def. È possibile eseguire questa operazione nel programma Visual Basic aggiungendo una clausola alias all'istruzione [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) .

## <a name="what-do-you-want-to-know-more-about"></a>Scegliere l'argomento su cui visualizzare maggiori informazioni

- [Esportazione da una DLL](exporting-from-a-dll.md)

- [Esportazione da una DLL utilizzando. File DEF](exporting-from-a-dll-using-def-files.md)

- [Esportazione da una DLL utilizzando __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Esportazione di funzioni C++ per l'utilizzo in eseguibili in linguaggio C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Determinare il metodo di esportazione da utilizzare](determining-which-exporting-method-to-use.md)

- [Nomi decorati](reference/decorated-names.md)

## <a name="see-also"></a>Vedere anche

[Creare DLL C/C++ in Visual Studio](dlls-in-visual-cpp.md)
