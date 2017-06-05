---
title: Classe basic_iostream | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::basic_iostream
- basic_iostream
- istream/std::basic_iostream::swap
dev_langs:
- C++
helpviewer_keywords:
- basic_iostream class
ms.assetid: 294b680b-eb49-4066-8db2-6d52dac9d6e3
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 3a71df6cc23c0c8f4e6faeb39474c363ed1bd412
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="basiciostream-class"></a>Classe basic_iostream
Classe di flusso che può eseguire operazioni sia di input sia di output.  
  
## <a name="syntax"></a>Sintassi  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_iostream : public basic_istream<Elem, Tr>,  
    public basic_ostream<Elem, Tr>  
{  
public:  
    explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

    virtual ~basic_iostream();

};  
```  
  
## <a name="remarks"></a>Note  
 La classe di modello descrive un oggetto che controlla gli inserimenti, attraverso la propria classe base [basic_ostream](../standard-library/basic-ostream-class.md)< `Elem`, `Tr`> e le estrazioni attraverso la propria classe base [basic_istream](../standard-library/basic-istream-class.md)< `Elem`, `Tr`>. I due oggetti condividono la classe base virtuale comune [basic_ios](../standard-library/basic-ios-class.md)< `Elem`, `Tr`>. I due oggetti gestiscono anche il buffer di un flusso comune, con elementi di tipo `Elem`, i cui tratti di carattere sono determinati dalla classe `Tr`. Il costruttore inizializza le proprie classi base attraverso `basic_istream`( **strbuf**) e `basic_ostream`( **strbuf**).  
  
### <a name="constructors"></a>Costruttori  
  
|||  
|-|-|  
|[basic_iostream](#basic_iostream)|Creare un oggetto `basic_iostream`.|  
  
### <a name="member-functions"></a>Funzioni membro  
  
|||  
|-|-|  
|[swap](#swap)|Scambia il contenuto dell'oggetto `basic_iostream` fornito con il contenuto di questo oggetto.|  
  
### <a name="operators"></a>Operatori  
  
|||  
|-|-|  
|[operator=](#op_eq)|Assegna il valore di un oggetto `basic_iostream` specificato a questo oggetto. Si tratta di un'assegnazione di spostamento che implica un oggetto `rvalue` che non lascia alcuna copia.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<istream>  
  
 **Spazio dei nomi:** std  
  
##  <a name="basic_iostream"></a>  basic_iostream::basic_iostream  
 Creare un oggetto `basic_iostream`.  
  
```  
explicit basic_iostream(basic_streambuf<Elem, Tr>* strbuf);

basic_iostream(basic_iostream&& right);

basic_iostream();
```  
  
### <a name="parameters"></a>Parametri  
 `strbuf`  
 Oggetto `basic_streambuf` esistente.  
  
 `right`  
 Un oggetto `basic_iostream` esistente usato per costruire una nuova classe `basic_iostream`.  
  
### <a name="remarks"></a>Note  
 Il primo costruttore inizializza gli oggetti base per mezzo di `basic_istream(strbuf)` e `basic_ostream(strbuf)`.  
  
 Il secondo costruttore inizializza gli oggetti base chiamando `move(right)`.  
  
##  <a name="op_eq"></a>  basic_iostream::operator=  
 Assegna il valore di un oggetto `basic_iostream` specificato a questo oggetto. Si tratta di un'assegnazione di spostamento che implica un riferimento rvalue che non lascia alcuna copia.  
  
```  
basic_iostream& operator=(basic_iostream&& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 Riferimento `rvalue` a un oggetto `basic_iostream` dal quale effettuare l'assegnazione.  
  
### <a name="remarks"></a>Note  
 L'operatore membro chiama `swap(right)`.  
  
##  <a name="swap"></a>  basic_iostream::swap  
 Scambia il contenuto dell'oggetto `basic_iostream` fornito con il contenuto di questo oggetto.  
  
```  
void swap(basic_iostream& right);
```  
  
### <a name="parameters"></a>Parametri  
 `right`  
 L'oggetto `basic_iostream` da scambiare.  
  
### <a name="remarks"></a>Note  
 La funzione membro chiama `swap(right)`.  
  
## <a name="see-also"></a>Vedere anche  
 [Thread safety nella libreria standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programmazione di iostream](../standard-library/iostream-programming.md)   
 [Convenzioni di iostream](../standard-library/iostreams-conventions.md)

