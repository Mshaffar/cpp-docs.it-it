---
title: Classe regex_iterator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- regex_iterator
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
dev_langs:
- C++
helpviewer_keywords:
- regex_iterator class
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: e73e90efd7248c6e8af5bfb406481623457c33c3
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="regexiterator-class"></a>Classe regex_iterator
Classe iterator per le corrispondenze.  
  
## <a name="syntax"></a>Sintassi  
```
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator {  
public:  
   typedef basic_regex<Elem, RXtraits> regex_type;  
   typedef match_results<BidIt> value_type;  
   typedef std::forward_iterator_tag iterator_category;  
   typedef std::ptrdiff_t difference_type;  
   typedef const match_results<BidIt>* pointer;  
   typedef const match_results<BidIt>& reference;  

   regex_iterator();
   regex_iterator(
      BidIt first, BidIt last, const regex_type& re,  
      regex_constants::match_flag_type f = regex_constants::match_default);

   bool operator==(const regex_iterator& right);
   bool operator!=(const regex_iterator& right);
   const match_results<BidIt>& operator*();
   const match_results<BidIt> * operator->();
   regex_iterator& operator++();
   regex_iterator& operator++(int);

private:
   BidIt begin; // exposition only  
   BidIt end; // exposition only  
   regex_type *pregex;     // exposition only  
   regex_constants::match_flag_type flags; // exposition only  
   match_results<BidIt> match; // exposition only  
   };  
```  
  
### <a name="parameters"></a>Parametri  
 `BidIt`  
 Tipo di iteratore per le sottocorrispondenze.  
  
 `Elem`  
 Tipo di elementi di cui trovare una corrispondenza.  
  
 `RXtraits`  
 Classe traits per gli elementi.  
  
## <a name="remarks"></a>Note  
 La classe modello descrive un oggetto iteratore costante in avanti. Estrae gli oggetti di tipo `match_results<BidIt>` applicando ripetutamente il relativo oggetto di espressione regolare `*pregex` alla sequenza di caratteri definita dall'intervallo dell'iteratore `[begin, end)`.  
  
## <a name="examples"></a>Esempi  
 Per esempi di espressioni regolari, vedere gli argomenti seguenti:  
  
- [regex_match](../standard-library/regex-functions.md#regex_match)  
  
- [regex_replace](../standard-library/regex-functions.md#regex_replace)  
  
- [regex_search](../standard-library/regex-functions.md#regex_search)  
  
- [swap](../standard-library/regex-functions.md#swap)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<regex>  
  
 **Spazio dei nomi:** std  
  
##  <a name="difference_type"></a>  regex_iterator::difference_type  
 Tipo di differenza iteratore.  
  
```  
typedef std::ptrdiff_t difference_type;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è sinonimo di `std::ptrdiff_t`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_difference_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="iterator_category"></a>  regex_iterator::iterator_category  
 Tipo della categoria di iteratore.  
  
```  
typedef std::forward_iterator_tag iterator_category;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è sinonimo di `std::forward_iterator_tag`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_iterator_category.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="op_neq"></a>  regex_iterator::operator!=  
 Confronta gli iteratori per verificarne la disuguaglianza.  
  
```  
bool operator!=(const regex_iterator& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Iteratore per il confronto.  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce `!(*this == right)`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_operator_ne.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="op_star"></a>  regex_iterator::operator*  
 Accede alla corrispondenza designata.  
  
```  
const match_results<BidIt>& operator*();
```  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce il valore `match`archiviato.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_operator_star.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="op_add_add"></a>  regex_iterator::operator++  
 Incrementa l'iteratore.  
  
```  
regex_iterator& operator++();
regex_iterator& operator++(int);
```  
  
### <a name="remarks"></a>Note  
 Se la corrispondenza corrente non contiene caratteri, il primo operatore chiama `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; in caso contrario, sposta il valore archiviato `begin` in modo che punti al primo carattere dopo la corrispondenza corrente e quindi chiama `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. Se la ricerca ha esito negativo, l'operatore imposta l'oggetto su un iteratore di fine sequenza. L'operatore restituisce l'oggetto.  
  
 Il secondo operatore esegue una copia dell'oggetto, incrementa l'oggetto, quindi restituisce la copia.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_operator_inc.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="op_eq"></a>  regex_iterator::operator=  
 Confronta gli iteratori per verificarne l'uguaglianza.  
  
```  
bool operator==(const regex_iterator& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Iteratore per il confronto.  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce true se `*this` e `right` sono iteratori di fine sequenza oppure se non è un iteratore di fine sequenza e `begin == right.begin`, `end == right.end`, `pregex == right.pregex`e `flags == right.flags`. In caso contrario, la funzione restituisce false.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_operator_as.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="regex_iterator__operator-_gt"></a>  regex_iterator::operator-&gt;  
 Accede alla corrispondenza designata.  
  
```  
const match_results<BidIt> * operator->();
```  
  
### <a name="remarks"></a>Note  
 La funzione membro restituisce l'indirizzo del valore archiviato `match`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_operator_arrow.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="pointer"></a>  regex_iterator::pointer  
 Tipo di un puntatore a una corrispondenza.  
  
```  
typedef match_results<BidIt> *pointer;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di `match_results<BidIt>*`, dove `BidIt` è il parametro di modello.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_pointer.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="reference"></a>  regex_iterator::reference  
 Tipo di un riferimento a una corrispondenza.  
  
```  
typedef match_results<BidIt>& reference;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di `match_results<BidIt>&`, dove `BidIt` è il parametro di modello.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_reference.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="regex_iterator"></a>  regex_iterator::regex_iterator  
 Costruisce l'iteratore.  
  
```  
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,  
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```  
  
### <a name="parameters"></a>Parametri  
 `first`  
 Inizio della sequenza per cui cercare una corrispondenza.  
  
 `last`  
 Fine della sequenza per cui cercare una corrispondenza.  
  
 `re`  
 Espressione regolare per le corrispondenze.  
  
 `f`  
 Flag per le corrispondenze.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore crea un iteratore di fine sequenza. Il secondo costruttore inizializza il valore archiviato `begin` con `first`, il valore archiviato `end` con `last`, il valore archiviato `pregex` con `&re`, e il valore archiviato `flags` con `f`. Quindi chiama `regex_search(begin, end, match, *pregex, flags)`. Se la ricerca ha esito negativo, il costruttore imposta l'oggetto su un iteratore di fine sequenza.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_construct.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="regex_type"></a>  regex_iterator::regex_type  
 Tipo dell'espressione regolare per cui cercare una corrispondenza.  
  
```  
typedef basic_regex<Elem, RXtraits> regex_type;  
```  
  
### <a name="remarks"></a>Note  
 typedef è sinonimo di `basic_regex<Elem, RXtraits>`.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_regex_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
##  <a name="value_type"></a>  regex_iterator::value_type  
 Tipo di una corrispondenza.  
  
```  
typedef match_results<BidIt> value_type;  
```  
  
### <a name="remarks"></a>Note  
 Il tipo è un sinonimo di `match_results<BidIt>`, dove `BidIt` è il parametro di modello.  
  
### <a name="example"></a>Esempio  
  
```cpp  
// std__regex__regex_iterator_value_type.cpp   
// compile with: /EHsc   
#include <regex>   
#include <iostream>   
  
typedef std::regex_iterator<const char *> Myiter;   
int main()   
    {   
    const char *pat = "axayaz";   
    Myiter::regex_type rx("a");   
    Myiter next(pat, pat + strlen(pat), rx);   
    Myiter end;   
  
    for (; next != end; ++next)   
        std::cout << "match == " << next->str() << std::endl;   
  
// other members   
    Myiter it1(pat, pat + strlen(pat), rx);   
    Myiter it2(it1);   
    next = it1;   
  
    Myiter::iterator_category cat = std::forward_iterator_tag();   
    Myiter::difference_type dif = -3;   
    Myiter::value_type mr = *it1;   
    Myiter::reference ref = mr;   
    Myiter::pointer ptr = &ref;   
  
    dif = dif; // to quiet "unused" warnings   
    ptr = ptr;   
  
    return (0);   
    }  
  
```  
  
```Output  
match == a  
match == a  
match == a  
```  
  
## <a name="see-also"></a>Vedere anche  
[\<regex>](../standard-library/regex.md)  
[Classe regex_constants](../standard-library/regex-constants-class.md)  
[Classe regex_error](../standard-library/regex-error-class.md)  
[Funzioni \<regex>](../standard-library/regex-functions.md)  
[Classe regex_iterator](../standard-library/regex-iterator-class.md)  
[Operatori \<regex>](../standard-library/regex-operators.md)  
[Classe regex_token_iterator](../standard-library/regex-token-iterator-class.md)  
[Classe regex_traits](../standard-library/regex-traits-class.md)  
[Typedef \<regex>](../standard-library/regex-typedefs.md)  

  
