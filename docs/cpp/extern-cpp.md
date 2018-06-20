---
title: extern (C++) | Documenti Microsoft
ms.custom: ''
ms.date: 04/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- extern
- extern_CPP
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b9f94d02443163f45b83d64702fe49622597cd
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36261077"
---
# <a name="extern-c"></a>extern (C++)

Il **extern** parola chiave viene applicato a una dichiarazione di modello, funzione o variabile globale per specificare che il nome di tale operazione ha *un collegamento esterno*. Per informazioni generali su un collegamento e perché è sconsigliato l'utilizzo di variabili globali, vedere [programma e collegamento](program-and-linkage-cpp.md).

Il **extern** parola chiave ha quattro significati a seconda del contesto:

1. in, una dichiarazione di variabili globale non const **extern** specifica che la variabile o la funzione viene definita in un'altra unità di conversione. Il **extern** devono essere applicati in tutti i file ad eccezione di quello in cui è definita la variabile.
1. in una dichiarazione di variabile const, specifica che la variabile è un collegamento esterno. Il **extern** deve essere applicata a tutte le dichiarazioni in tutti i file. (Le variabili const globali dispongono di collegamento interno per impostazione predefinita).
1. **extern "C"** specifica che la funzione definita altrove e utilizza la convenzione di chiamata del linguaggio C. Il modificatore di extern "C" può essere applicato anche a più dichiarazioni di funzione in un blocco.
1. in una dichiarazione di modello, specifica che il modello è già stata creata un'istanza in un' posizione. Si tratta di un'ottimizzazione che indica al compilatore che possono riutilizzare la creazione dell'istanza anziché crearne uno nuovo nella posizione corrente. Per ulteriori informazioni su questo utilizzo di **extern**, vedere [modelli](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>collegamento di extern per variabili globali non const

Quando il linker rileva **extern** prima di una dichiarazione di variabile globale, Cerca la definizione in un'altra unità di conversione. Le dichiarazioni di variabili non const in ambito globale sono esterne per impostazione predefinita. si applicano solo **extern** alle dichiarazioni che non consentono la definizione.

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="extern-linkage-for-const-globals"></a>collegamento di extern per globals const

Un **const** (variabile globale) contiene un collegamento interno per impostazione predefinita. Se si desidera che la variabile ad avere un collegamento esterno, applicare il **extern** parola chiave per la definizione anche tutte le altre dichiarazioni in altri file:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>Collegamento constexpr extern

In Visual Studio 2017 15.3 e versioni precedenti, il compilatore ha sempre fornito di un collegamento interno variabili constexpr anche quando la variabile è stato contrassegnato come esterno. In Visual Studio 2017 versione 15.5 una nuova opzione del compilatore ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) abilita il comportamento corretto conforme agli standard. Questo diventerà infine il comportamento predefinito.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Se un file di intestazione contiene una variabile dichiarata extern constexpr, deve essere contrassegnato **__declspec(selectany)** per avere correttamente relative dichiarazioni duplicati combinati:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>dichiarazioni di funzione di tipo extern "C" e "C++" extern

 In C++, quando usato con una stringa **extern** specifica che per i dichiaratori vengono usate le convenzioni di un collegamento di un'altra lingua. Alle funzioni e ai dati C è possibile accedere solo se in precedenza sono stati dichiarati come dotati di collegamento a C. Tuttavia, devono essere definiti in una unità di conversione compilata separatamente.

 Microsoft C++ supporta le stringhe **"C"** e **"C++"** nel *valore letterale stringa* campo. Tutte dello standard includono file usano il **extern** sintassi "C" per consentire le funzioni della libreria di runtime da utilizzare nei programmi C++.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato come dichiarare nomi con collegamento C:

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions 
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

 Se una funzione contiene più specifiche di collegamento, queste devono concordare; è un errore dichiarare le funzioni come dotate sia di collegamento C++ che C. Inoltre, se due dichiarazioni per una funzione si verificano in un programma - una con una specifica di collegamento e una senza - la dichiarazione con la specifica di collegamento deve essere specificata per prima. A tutte le dichiarazioni ridondanti di funzioni che hanno già specifiche di collegamento viene fornito il collegamento specificato nella prima dichiarazione. Ad esempio:

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Vedere anche

- [Parole chiave](../cpp/keywords-cpp.md)
- [Programma e collegamento](program-and-linkage-cpp.md)
- [Identificatore di classe di archiviazione c extern](../c-language/extern-storage-class-specifier.md) 
- [Comportamento degli identificatori nel linguaggio C](../c-language/behavior-of-identifiers.md) 
- [Collegamenti in C](../c-language/linkage.md)