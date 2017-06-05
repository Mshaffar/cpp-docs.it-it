---
title: "dllexport, dllimport | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "dllimport_cpp"
  - "dllexport_cpp"
  - "dllexport"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (parola chiave) [C++], dllexport"
  - "__declspec (parola chiave) [C++], dllimport"
  - "dllexport __declspec (parola chiave)"
  - "dllimport __declspec (parola chiave)"
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# dllexport, dllimport
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Sezione specifica Microsoft**  
  
 Gli attributi della classe di archiviazione `dllexport` e **dllimport** sono estensioni specifiche di Microsoft ai linguaggi C e C\+\+.  È possibile usarli per esportare e importare funzioni, dati e oggetti verso o da una DLL.  
  
## Sintassi  
  
```  
  
        __declspec( dllimport ) declarator  
__declspec( dllexport ) declarator  
```  
  
## Note  
 Questi attributi definiscono in modo esplicito l'interfaccia della DLL per il client che può essere il file eseguibile o un'altra DLL.  La dichiarazione delle funzioni come `dllexport` elimina la necessità di un file def di definizione moduli, almeno rispetto alla specifica delle funzioni esportate.  L'attributo `dllexport` sostituisce la parola chiave `__export`.  
  
 Se la classe è contrassegnata come declspec\(dllexport\), tutte le specializzazioni dei modelli di classe nella gerarchia di classe vengono implicitamente contrassegnate come declspec\(dllexport\).  Ciò significa che le istanze dei modelli di classe vengono create in modo esplicito e che i membri della classe devono essere definiti.  
  
 `dllexport` di una funzione espone la funzione con il relativo nome decorato.  Per le funzioni C\+\+, ciò include l'alterazione del nome.  Per le funzioni C o le funzioni dichiarate come `extern "C"`, ciò include la decorazione specifica della piattaforma basata sulla convenzione di chiamata.  Per informazioni sulla decorazione dei nomi nel codice C\/C\+\+, vedere [Nomi decorati](../build/reference/decorated-names.md).  Nessuna decorazione dei nomi viene applicata alle funzioni C esportate o alle funzioni `extern "C"` C\+\+ che usano la convenzione di chiamata `__cdecl`.  
  
 Per esportare un nome non decorato, è possibile creare un collegamento usando un file di definizione del modulo \(con estensione def\), che definisce il nome non decorato in una sezione EXPORTS.  Per altre informazioni, vedere [EXPORTS](../build/reference/exports.md).  Per esportare un nome non decorato è anche possibile usare una direttiva `#pragma comment(linker, "/export:``alias``=``decorated_name``")` nel codice sorgente.  
  
 Quando si dichiara `dllexport` o **dllimport**, è necessario usare la [sintassi degli attributi estesa](../cpp/declspec.md) e la parola chiave `__declspec`.  
  
## Esempio  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 In alternativa, per rendere il codice più leggibile, è possibile usare le definizioni di macro:  
  
```cpp  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllImport int j;  
DllExport int n;  
```  
  
 Per altre informazioni, vedere:  
  
-   [Definizioni e dichiarazioni](../cpp/definitions-and-declarations-cpp.md)  
  
-   [Definizione delle funzioni C\+\+ inline con dllexport e dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
-   [Regole e limitazioni generali](../cpp/general-rules-and-limitations.md)  
  
-   [Utilizzo di dllimport e dllexport nelle classi C\+\+](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)  
  
 **Fine sezione specifica Microsoft**  
  
## Vedere anche  
 [\_\_declspec](../cpp/declspec.md)   
 [Parole chiave C\+\+](../cpp/keywords-cpp.md)