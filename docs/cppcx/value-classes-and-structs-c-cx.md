---
title: "Classi e struct di valore (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "value struct"
  - "value class"
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
caps.latest.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 12
---
# Classi e struct di valore (C++/CX)
Uno *struct di valore* o una *classe di valore* è una struttura POD \(Plain Old Data\) compatibile con [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] con una dimensione fissa e costituita solo da campi; a differenza di una classe di riferimento, non dispone di proprietà.  
  
 Gli esempi seguenti mostrano come dichiarare e inizializzare struct di valore.  
  
```  
  
// in mainpage.xaml.h: value struct TestStruct { Platform::String^ str; int i; }; value struct TestStruct2 { TestStruct ts; Platform::String^ str; int i; }; // in mainpage.cpp: // Initialize a value struct with an int and String TestStruct ts = {"I am a TestStruct", 1}; // Initialize a value struct that contains // another value struct, an int and a String TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2}; // Initialize value struct members individually. TestStruct ts3; ts3.i = 108; ts3.str = "Another way to init a value struct.";  
  
```  
  
 Quando una variabile di un tipo di valore viene assegnata a un'altra variabile, il valore viene copiato. In tal modo ciascuna delle due variabili dispone di una propria copia dei dati. Uno *struct di valore* è una struttura di dimensione fissa che contiene solo campi di dati pubblici e viene dichiarata utilizzando la parola chiave `value struct`.  
  
 Una *classe di valore* è analoga a uno `value struct`, eccetto per il fatto che ai relativi campi deve essere concessa esplicitamente l'accessibilità pubblica. La classe viene dichiarata utilizzando la parola chiave `value class`.  
  
 Uno struct o una classe di valore può contenere come campi solo tipi numerici fondamentali, classi di enumerazione, `Platform::String^` o [Platform::IBox \<T\>^](../cppcx/platform-ibox-interface.md), dove T è un tipo numerico o una classe di enumerazione o uno struct o una classe di valore. Un campo `IBox<T>^` può contenere un valore `nullptr`. Ecco come C\+\+ implementa il concetto di *tipi di valore nullable*.  
  
 Uno struct o una classe di valori che contiene un tipo `Platform::String^` o `IBox<T>^` come membro non supporta `memcpy`.  
  
 Poiché tutti i membri di una `value class` o di uno `value struct` sono pubblici e vengono generati nei metadati, i tipi C\+\+ standard non sono consentiti come membri. Non è così per le classi di riferimento che possono contenere tipi C\+\+ standard `private` o `internal`.  
  
 Nel frammento di codice riportato di seguito i tipi `Coordinates` e `City` vengono dichiarati come struct di valore. Nota che uno dei membri dati `City` è un tipo `GeoCoordinates`. Uno `value struct` può contenere altri struct di valore come membri.  
  
 [!code-cpp[cx_classes#07](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.h#07)]  
  
## Passaggio dei parametri per i tipi valore  
 Se si ha un tipo valore come parametro di funzione o di metodo, normalmente viene passato per valore. Per gli oggetti di grandi dimensioni, tuttavia, questo può causare un problema di prestazioni. In Visual Studio2013 e versioni precedenti, i tipi valore in C\+\+\/CX vengono sempre passati per valore. In Visual Studio 2015 e versioni successive, è possibile passare i tipi valore per riferimento oppure per valore.  
  
 Per dichiarare un parametro che passa un tipo valore per valore, usare codice simile al seguente:  
  
```  
void Method1(MyValueType obj);  
```  
  
 Per dichiarare un parametro che passa un tipo valore per riferimento, usa il simbolo di riferimento \(&\), come illustrato di seguito:  
  
```  
void Method2(MyValueType& obj);  
```  
  
 Il tipo in Method2 è un riferimento a MyValueType e funziona esattamente come un tipo di riferimento nel linguaggio C\+\+ standard.  
  
 Quando si chiama Method1 da un altro linguaggio, ad esempio C\#, non è necessario usare la parola chiave `ref` o `out`. Quando si chiama Method2, usare la parola chiave `ref`.  
  
```  
Method2(ref obj);  
```  
  
 Per passare un tipo valore per riferimento è possibile usare anche un simbolo puntatore \(\*\). Il comportamento rispetto ai chiamanti in altri linguaggi è lo stesso \(i chiamanti in C\# usano la parola chiave `ref`\), ma nel metodo il tipo è un puntatore al tipo valore.  
  
## Tipi di valori nullable  
 Come accennato in precedenza, una classe o uno struct di valori può presentare un campo di tipo [Platform::IBox\<T\>^](../cppcx/platform-ibox-interface.md), ad esempio `IBox<int>^`. A tale campo può essere assegnato qualsiasi valore numerico valido per il tipo `int` o un valore `nullptr`. È possibile passare un campo nullable come argomento a un metodo il cui parametro è dichiarato come facoltativo o qualsiasi altra posizione in cui un tipo di valore non deve necessariamente avere un valore.  
  
 L'esempio seguente mostra come inizializzare uno struct con un campo nullable.  
  
```  
public value struct Student { Platform::String^ Name; int EnrollmentYear; Platform::IBox<int>^ GraduationYear; // Null if not yet graduated. }; //To create a Student struct, one must populate the nullable type. MainPage::MainPage() { InitializeComponent(); Student A; A.Name = "Alice"; A.EnrollmentYear = 2008; A.GraduationYear = ref new Platform::Box<int>(2012); Student B; B.Name = "Bob"; B.EnrollmentYear = 2011; B.GraduationYear = nullptr; IsCurrentlyEnrolled(A); IsCurrentlyEnrolled(B); } bool MainPage::IsCurrentlyEnrolled(Student s) { if (s.GraduationYear == nullptr) { return true; } return false; }  
  
```  
  
 Uno struct di valori può essere reso nullable in modo analogo, come illustrato di seguito:  
  
```  
  
public value struct MyStruct { public: int i; Platform::String^ s; }; public ref class MyClass sealed { public: property Platform::IBox<MyStruct>^ myNullableStruct; };  
```  
  
## Vedere anche  
 [Sistema di tipi \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Riferimenti al linguaggio Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Riferimenti a spazi dei nomi](../cppcx/namespaces-reference-c-cx.md)   
 [Classi e struct di riferimento \(C\+\+\/CX\)](../cppcx/ref-classes-and-structs-c-cx.md)