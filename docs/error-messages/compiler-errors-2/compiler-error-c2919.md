---
title: Errore del compilatore C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: 624b3ab47ccb1c934b612ec8648b5eee0d233690
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176975"
---
# <a name="compiler-error-c2919"></a>Errore del compilatore C2919

'type': impossibile utilizzare operatori sulla superficie pubblicata di un tipo WinRT

Il sistema di tipo Windows Runtime non supporta funzioni membro di operatore nella superficie pubblicata di un tipo. Infatti, non tutti i linguaggi possono utilizzare funzioni membro di operatore. È possibile creare funzioni membro di operatore private o interne che possono essere chiamate dal codice C++ nella stessa classe o unità di compilazione.

Per risolvere il problema, rimuovere la funzione membro di operatore dall'interfaccia pubblica o sostituirla con una funzione membro denominata. Ad esempio, invece di `operator==`, assegnare alla funzione membro il nome `Equals`.
