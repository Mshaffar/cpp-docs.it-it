---
title: Assembly misti (nativi e gestiti)
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: 11bdfc98c64b2612129e10c002c68ee243bec7da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311808"
---
# <a name="mixed-native-and-managed-assemblies"></a>Assembly misti (nativi e gestiti)

Gli assembly misti sono in grado di contenere sia istruzioni per computer non gestite che istruzioni MSIL. Ciò consente di chiamare e essere chiamati dai componenti .NET, mantenendo la compatibilità con le librerie native C++ . Utilizzando assembly misti, gli sviluppatori possono creare applicazioni utilizzando una combinazione di codice .NET C++ e codice nativo.

Ad esempio, una libreria esistente costituita interamente da codice C++ nativo può essere portata alla piattaforma .NET ricompilando solo un modulo con l'opzione **/CLR** del compilatore. Questo modulo è quindi in grado di usare le funzionalità di .NET, ma rimane compatibile con il resto dell'applicazione. È anche possibile decidere tra la compilazione gestita e nativa in base a una funzione all'interno dello stesso file (vedere [gestito, non gestito](../preprocessor/managed-unmanaged.md)).

L' C++ oggetto visivo supporta solo la generazione di assembly gestiti misti utilizzando l'opzione del compilatore **/CLR** . Le opzioni del compilatore **/CLR: pure** e **/CLR: safe** sono deprecate in Visual Studio 2015 e non supportate in Visual Studio 2017. Se sono necessari assembly gestiti puri o verificabili, è consigliabile crearli usando C#.

Le versioni precedenti del set C++ di strumenti del compilatore Microsoft supportano la generazione di tre tipi distinti di assembly gestiti, ovvero mista, pura e verificabile. Gli ultimi due sono descritti in [codice pure e verificabile (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>Contenuto della sezione

[Procedura: Esegui la migrazione a/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Vengono descritti i passaggi consigliati per l'introduzione o l'aggiornamento della funzionalità .NET nell'applicazione.

[Procedura: Compilare codice MFC e ATL utilizzando/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Viene illustrato come compilare programmi MFC e ATL esistenti per la destinazione di Common Language Runtime.

[Inizializzazione di assembly misti](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Descrive le soluzioni e il problema "blocco del caricatore".

[Supporto delle librerie per assembly misti](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Viene illustrato come utilizzare le librerie native nelle compilazioni **/CLR** .

[Considerazioni sulle prestazioni](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Descrive le implicazioni relative alle prestazioni di assembly misti e di marshalling dei dati.

[Domini applicazione e Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Viene illustrato C++ il supporto visivo per i domini applicazione.

[Doppio thunk](../dotnet/double-thunking-cpp.md)<br/>
Vengono illustrate le implicazioni relative alle prestazioni di un punto di ingresso nativo per una funzione gestita.

[Evitare eccezioni all'arresto di CLR quando si utilizzano oggetti COM compilati con/CLR](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Viene descritto come garantire l'arresto corretto di un'applicazione gestita che utilizza un oggetto COM compilato con **/CLR**.

[Procedura: Creare un'applicazione parzialmente attendibile rimuovendo la dipendenza dalla DLL della libreria CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
Viene illustrato come creare un'applicazione Common Language Runtime parzialmente attendibile usando C++ visuale rimuovendo la dipendenza da msvcm90. dll.

Per ulteriori informazioni sulle linee guida per la codifica per gli assembly misti, vedere l'articolo MSDN [Panoramica sull'interoperabilità del codice gestito/non gestito](/previous-versions/dotnet/articles/ms973872(v=msdn.10)).

## <a name="see-also"></a>Vedere anche

- [Interoperabilità .NET e nativa](../dotnet/native-and-dotnet-interoperability.md)
