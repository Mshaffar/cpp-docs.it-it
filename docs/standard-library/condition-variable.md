---
title: '&lt;condition_variable&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <condition_variable>
dev_langs:
- C++
ms.assetid: 8567f7cc-20bd-42a7-9137-87c46f878009
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 6002dcd4cd0fe35c99ce56a1d9fd3b5f3c23dd08
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="ltconditionvariablegt"></a>&lt;condition_variable&gt;
Definisce le classi [condition_variable](../standard-library/condition-variable-class.md) e [condition_variable_any](../standard-library/condition-variable-any-class.md) che vengono usate per creare oggetti che attendono che una condizione diventi true.  
  
 Questa intestazione usa il runtime di concorrenza (ConcRT) in modo da essere utilizzabile con altri meccanismi ConcRT. Per altre informazioni su ConcRT, vedere [Runtime di concorrenza](../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
#include <condition_variable>  
```  
  
> [!NOTE]
>  Nel codice che viene compilato mediante **/clr**, questa intestazione è bloccata.  
  
### <a name="remarks"></a>Note  
 Il codice che è in attesa di una variabile di condizione deve usare anche un `mutex`. Un thread chiamante deve bloccare il `mutex` prima di chiamare le funzioni di attesa per la variabile di condizione. In seguito il `mutex` viene bloccato quando la funzione chiamata viene restituita. Il `mutex` non risulta bloccato mentre il thread è in attesa che la condizione diventi true. Per far sì che non vi siano risultati imprevedibili, tutti i thread in attesa di una variabile di condizione devono usare lo stesso oggetto `mutex`.  
  
 Gli oggetti di tipo `condition_variable_any` possono essere usati con un mutex di qualsiasi tipo. Il tipo di mutex usato non deve necessariamente specificare il metodo `try_lock`. Gli oggetti di tipo `condition_variable` possono essere usati solo con un mutex di tipo `unique_lock<mutex>`. Gli oggetti di questo tipo possono risultare più veloci rispetto agli oggetti di tipo `condition_variable_any<unique_lock<mutex>>`.  
  
 Per attendere un evento, per prima cosa bloccare il mutex e quindi chiamare uno dei metodi `wait` sulla variabile di condizione. La chiamata `wait` si blocca fino a quando un altro thread segnala la variabile di condizione.  
  
 Si verificano *riattivazioni spurie* quando i thread in attesa di variabili di condizione si sbloccano senza le notifiche appropriate. Per riconoscere tali riattivazioni spurie, il codice che è in attesa che una condizione diventi true deve verificare in modo esplicito la condizione quando il codice viene restituito da una funzione di attesa. Ciò avviene solitamente usando un ciclo. Per eseguire il ciclo, è possibile usare `wait(unique_lock<mutex>& lock, Predicate pred)`.  
  
```cpp  
while (condition is false)
    wait for condition variable;
```  
  
 Le classi `condition_variable_any` e `condition_variable` hanno tre metodi che attendono una condizione.  
  
- `wait` attende per un periodo di tempo illimitato.  
  
- `wait_until` attende fino a una condizione `time` specifica.  
  
- `wait_for` attende una condizione `time interval` specifica.  
  
 Ognuno di questi metodi ha due versioni di overload. Una si limita ad attendere e può riattivarsi in modo spurio. L'altra accetta un argomento di modello aggiuntivo che definisce un predicato. Il metodo non restituisce alcun valore finché il predicato non è `true`.  
  
 Ogni classe include anche due metodi che vengono usati per notificare a una variabile di condizione che la condizione è `true`.  
  
- `notify_one` attiva uno dei thread in attesa della variabile di condizione.  
  
- `notify_all` attiva tutti i thread in attesa della variabile di condizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Header Files Reference](../standard-library/cpp-standard-library-header-files.md)  (Riferimento file di intestazione)  
 [Classe condition_variable](../standard-library/condition-variable-class.md)   
 [Classe condition_variable_any](../standard-library/condition-variable-any-class.md)
