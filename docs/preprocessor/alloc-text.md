---
title: Pragma alloc_text
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 7ddb12b39e068dea42f7a47f7fd937424be43725
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216347"
---
# <a name="alloc_text-pragma"></a>Pragma alloc_text

Assegnare un nome alla sezione di codice in cui devono essere presenti le definizioni di funzioni specificate. Il pragma deve essere trovarsi tra un dichiaratore di funzione e la definizione di funzione per le funzioni denominate.

## <a name="syntax"></a>Sintassi

> **#pragma alloc_text (** "*textsection*" **,** *funzione1* [ **,** *funzione2* ...] **)**

## <a name="remarks"></a>Note

Il pragma **alloc_text** non gestisce C++ funzioni membro o funzioni in overload. Si applica solo alle funzioni dichiarate con il collegamento C, ovvero funzioni dichiarate con la specifica di collegamento **extern "C"** . Se si tenta di utilizzare questo pragma in una funzione con collegamento C++, viene generato un errore del compilatore.

Poiché l'indirizzamento `__based` della funzione using non è supportato, per specificare le posizioni della sezione è necessario usare il pragma **alloc_text** . Il nome specificato da *textsection* deve essere racchiuso tra virgolette doppie.

Il pragma **alloc_text** deve essere visualizzato dopo le dichiarazioni di una delle funzioni specificate e prima delle definizioni di queste funzioni.

Le funzioni a cui viene fatto riferimento in un pragma **alloc_text** devono essere definite nello stesso modulo del pragma. In caso contrario, se una funzione non definita viene compilata in un secondo momento in un'altra sezione di testo, è possibile che l'errore non venga intercettato. Sebbene il programma in genere venga eseguito correttamente, la funzione non verrà allocata nelle sezioni desiderate.

Di seguito sono riportate altre limitazioni relative a **alloc_text** :

- Non può essere usato all'interno di una funzione.

- Deve essere utilizzato dopo che la funzione è stata dichiarata, ma prima che la funzione sia stata definita.

## <a name="see-also"></a>Vedere anche

[Direttive pragma e parola chiave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
