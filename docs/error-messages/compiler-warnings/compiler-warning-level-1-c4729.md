---
title: Avviso del compilatore (livello 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: e78606f117251fa8ab1f08f2cef280a266309c32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185828"
---
# <a name="compiler-warning-level-1-c4729"></a>Avviso del compilatore (livello 1) C4729

funzione troppo grande per avvisi basati su grafico del flusso

Questo avviso viene generato quando una funzione è troppo grande per essere compilata con il controllo affidabile per le situazioni in cui verrebbe generato un avviso. L'avviso viene generato solo quando viene usata l'opzione [/Od](../../build/reference/od-disable-debug.md) del compilatore.

Per risolvere il problema, suddividere la funzione in funzioni più piccole.
