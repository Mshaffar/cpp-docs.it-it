---
title: "Operatore di risoluzione dell&#39;ambito: :: | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "::"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ":: (operatore)"
  - "operatori [C++], risoluzione ambito"
  - "operatore di risoluzione dell'ambito"
  - "ambito, operatore di risoluzione dell'ambito"
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Operatore di risoluzione dell&#39;ambito: ::
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

L'operatore di risoluzione dell'ambito `::` viene usato per identificare e risolvere l'ambiguità degli identificatori usati in diversi ambiti.  Per altre informazioni sull'ambito, vedere [Ambito](../cpp/scope-visual-cpp.md).  
  
## Sintassi  
  
```  
:: identifier class-name :: identifier namespace :: identifier enum class :: identifier enum struct :: identifier  
```  
  
## Note  
 `identifier` può essere una variabile una funzione oppure un valore di enumerazione.  
  
## Con classi e spazi dei nomi  
 L'esempio seguente mostra in che modo l'operatore di risoluzione dell'ambito viene usato con gli spazi dei nomi e le classi:  
  
```cpp  
namespace NamespaceA{  
    int x;  
    class ClassA {  
    public:  
        int x;  
    };  
}  
  
int main() {  
  
    // A namespace name used to disambiguate  
    NamespaceA::x = 1;  
  
    // A class name used to disambiguate  
    NamespaceA::ClassA a1;  
    a1.x = 2;  
  
}  
  
```  
  
 Un operatore di risoluzione dell'ambito senza un qualificatore dell'ambito fa riferimento allo spazio dei nomi globale.  
  
```cpp  
namespace NamespaceA{  
    int x;  
}  
  
int x;   
  
int main() {  
    int x;  
  
    // the x in main()  
    x = 0;   
    // The x in the global namespace  
    ::x = 1;   
  
    // The x in the A namespace  
    NamespaceA::x = 2;   
}  
```  
  
 È possibile usare l'operatore di risoluzione dell'ambito per identificare un membro di uno spazio dei nomi oppure per identificare uno spazio dei nomi che nomina lo spazio dei nomi del membro in una direttiva using.  Nell'esempio seguente, è possibile usare `NamespaceC` per qualificare `ClassB`, anche se `ClassB` è stato dichiarato in uno spazio dei nomi`NamespaceB`, perché `NamespaceB` è stato nominato in `NamespaceC` da una direttiva using.  
  
```cpp  
namespace NamespaceB {  
    class ClassB {  
    public:  
        int x;  
    };  
}  
  
namespace NamespaceC{  
    using namespace B;  
  
}  
int main() {  
    NamespaceB::ClassB c_b;  
    NamespaceC::ClassB c_c;  
  
    c_b.x = 3;  
    c_c.x = 4;  
}  
  
```  
  
 È possibile usare catene di operatori di risoluzione dell'ambito.  Nell'esempio seguente, `NamespaceD::NamespaceD1` identifica lo spazio dei nomi annidato `NamespaceD1` e `NamespaceE::ClassE::ClassE1` identifica la classe annidata `ClassE1`.  
  
```cpp  
namespace NamespaceD{  
    namespace NamespaceD1{  
        int x;  
    }  
}  
  
namespace NamespaceE{  
  
    class ClassE{  
    public:  
        class ClassE1{  
        public:  
            int x;  
        };  
    };  
}  
  
int main() {  
    NamespaceD:: NamespaceD1::x = 6;  
    NamespaceE::ClassE::ClassE1 e1;  
    e1.x = 7  ;  
}  
  
```  
  
## Con membri statici  
 Per chiamare i membri statici delle classi è necessario usare l'operatore di risoluzione dell'ambito.  
  
```cpp  
class ClassG {  
public:  
    static int get_x() { return x;}  
    static int x;  
};  
  
int ClassG::x = 6;  
  
int main() {  
  
    int gx1 = ClassG::x;  
    int gx2 = ClassG::get_x();   
}  
  
```  
  
## Con enumerazioni con ambito  
 L'operatore di risoluzione dell'ambito è anche usato con i valori di un'enumerazione con ambito \([Dichiarazioni di enumerazioni](../cpp/enumerations-cpp.md)\), come nell'esempio seguente:  
  
```cpp  
enum class EnumA{  
    First,  
    Second,  
    Third  
};  
  
int main() {  
  
    EnumA enum_value = EnumA::First;  
}  
  
```  
  
## Vedere anche  
 [Operatori C\+\+, precedenza e associazione](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Spazi dei nomi](../cpp/namespaces-cpp.md)   
 [Nomi e nomi completi](../misc/names-and-qualified-names.md)