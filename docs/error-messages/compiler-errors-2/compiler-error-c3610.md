---
title: Errore del compilatore C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 9965e6420171b2ea48c8fb7bacc0a5a37ea2f227
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344601"
---
# <a name="compiler-error-c3610"></a>Errore del compilatore C3610

'valuetype': tipo di valore deve essere 'boxed' prima di poter chiamare il 'metodo metodo'

Per impostazione predefinita, un tipo di valore non è nell'heap gestito. Prima di chiamare i metodi da classi di runtime .NET, ad esempio `Object`, è necessario spostare il tipo di valore nell'heap gestito.

È raggiungibile tramite l'opzione del compilatore obsolete solo C3610 **/CLR: oldSyntax**.
