---
title: Compilatore avviso (livello 1) C4729 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: 7
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 57a83903ac31b7f05ee1892cca011c9ef9d8fe74
ms.contentlocale: it-it
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4729"></a>Avviso del compilatore (livello 1) C4729
funzione troppo grande per avvisi basati su grafico del flusso  
  
 Questo avviso viene generato quando una funzione è troppo grande per essere compilata con il controllo affidabile per le situazioni in cui verrebbe generato un avviso. Questo avviso è generato quando il [/Od](../../build/reference/od-disable-debug.md) utilizzata l'opzione del compilatore.  
  
 Per risolvere il problema, suddividere la funzione in funzioni più piccole.