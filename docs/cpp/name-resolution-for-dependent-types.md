---
title: Risoluzione dei nomi per tipi dipendenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d8978e38745f088884bbf28ffb0ab98cfb87895
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="name-resolution-for-dependent-types"></a>Risoluzione dei nomi per tipi dipendenti
Utilizzare **typename** per i nomi completi nelle definizioni di modello per indicare al compilatore che il nome completo specificato identifica un tipo. Per ulteriori informazioni, vedere [typename](../cpp/typename.md).  
  
```cpp  
// template_name_resolution1.cpp  
#include <stdio.h>  
template <class T> class X  
{  
public:  
   void f(typename T::myType* mt) {}  
};  
  
class Yarg  
{  
public:  
   struct myType { };  
};  
  
int main()  
{  
   X<Yarg> x;  
   x.f(new Yarg::myType());  
   printf("Name resolved by using typename keyword.");  
}  
```  
  
```Output  
Name resolved by using typename keyword.  
```  
  
 Ricerca del nome per i nomi dipendenti esamina i nomi sia dal contesto della definizione del modello, nell'esempio seguente, in questo contesto cercherebbe `myFunction(char)`e il contesto dell'istanza del modello. Nell'esempio seguente, il modello viene creata un'istanza; Pertanto, il `MyNamespace::myFunction` è visibile dal punto di creazione dell'istanza e viene selezionato come corrispondenza ottimale. Se `MyNamespace::myFunction` è stato rinominato, in alternativa viene chiamato `myFunction(char)`.  
  
 Tutti i nomi vengono risolti come se fossero nomi dipendenti. Tuttavia, è consigliabile utilizzare nomi completi se è possibile che si verifichi un conflitto.  
  
```cpp  
// template_name_resolution2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void myFunction(char)  
{  
   cout << "Char myFunction" << endl;  
}  
  
template <class T> class Class1  
{  
public:  
   Class1(T i)  
   {  
      // If replaced with myFunction(1), myFunction(char)  
      // will be called  
      myFunction(i);  
}  
};  
  
namespace MyNamespace  
{  
   void myFunction(int)  
   {  
      cout << "Int MyNamespace::myFunction" << endl;  
   }  
};  
  
using namespace MyNamespace;  
  
int main()  
{  
   Class1<int>* c1 = new Class1<int>(100);  
}  
```  
  
### <a name="output"></a>Output  
  
```  
Int MyNamespace::myFunction  
```  
  
### <a name="template-disambiguation"></a>Risoluzione dell'ambiguità del modello  
 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] applica le regole standard C++98/03/11 per la risoluzione dell'ambiguità con la parola chiave "template". Nell'esempio seguente, Visual C++ 2010 accetta le righe non sia le righe conformi.  [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]accetta solo le righe conformi.  
  
```cpp  
#include <iostream>  
#include <ostream>  
#include <typeinfo>  
using namespace std;  
  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    #if defined(NONCONFORMANT)  
        typedef typename AY::Rebind<X>::Other AX; // nonconformant  
    #elif defined(CONFORMANT)  
        typedef typename AY::template Rebind<X>::Other AX; // conformant  
    #else  
        #error Define NONCONFORMANT or CONFORMANT.  
    #endif  
};  
  
int main() {  
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;  
}  
```  
  
 La conformità alle regole di risoluzione ambiguità è necessaria perché, per impostazione predefinita, in C++ si presuppone che `AY::Rebind` non sia un modello e quindi il compilatore interpreta "`<`" come minore di. È necessario indicare che `Rebind` è un modello in modo da poter analizzare correttamente "`<`" come parentesi angolare.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei nomi](../cpp/templates-and-name-resolution.md)