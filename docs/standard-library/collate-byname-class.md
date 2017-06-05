---
title: Classe collate_byname | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- locale/std::collate_byname
- collate_byname
dev_langs:
- C++
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: 24
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
ms.openlocfilehash: 0552fd2b76859166ea84ec17433ee5d04b5dcb19
ms.contentlocale: it-it
ms.lasthandoff: 04/29/2017

---
# <a name="collatebyname-class"></a>Classe collate_byname
Classe modello derivata che descrive un oggetto che può essere utilizzato come facet di ordinamento delle impostazioni locali specificate, consentendo il recupero di informazioni relative alle convenzioni di ordinamento delle stringhe specifiche di un'area culturale.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```  
  
#### <a name="parameters"></a>Parametri  
 `_Locname`  
 Impostazioni locali denominate.  
  
 `_Refs`  
 Conteggio di riferimento iniziale.  
  
## <a name="remarks"></a>Note  
 La classe modello descrive un oggetto che può fungere da [facet delle impostazioni locali](../standard-library/locale-class.md#facet_class) di tipo [collate](../standard-library/collate-class.md#collate)\<CharType>. Il comportamento è determinato dalle [impostazioni locali denominate](../standard-library/locale-class.md#name)`_Locname`. Ogni costruttore inizializza l'oggetto di base con [collate](../standard-library/collate-class.md#collate)\<CharType> (`_Refs`).  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<locale>  
  
 **Spazio dei nomi:** std  
  
## <a name="see-also"></a>Vedere anche  
 [Thread Safety in the C++ Standard Library](../standard-library/thread-safety-in-the-cpp-standard-library.md) (Thread safety nella libreria standard C++)



