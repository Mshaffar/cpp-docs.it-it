---
title: Forme obsolete di dichiarazioni e definizioni di funzioni
ms.date: 11/04/2016
helpviewer_keywords:
- old style function declarations
ms.assetid: 67c5038f-0529-4f29-9d0f-c27580977b50
ms.openlocfilehash: f26e79a586ea451cc51b339b5be593c2359e1f1a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745881"
---
# <a name="obsolete-forms-of-function-declarations-and-definitions"></a>Forme obsolete di dichiarazioni e definizioni di funzioni

Rispetto alla sintassi consigliata dallo standard ANSI C, le dichiarazioni e le definizioni delle funzioni obsolete utilizzano regole leggermente differenti per la dichiarazione dei parametri. Innanzitutto, le dichiarazioni obsolete non includono un elenco di parametri. In secondo luogo, nella definizione di funzione, i parametri sono elencati, ma i relativi tipi sono dichiarati nell'elenco di parametri. Le dichiarazioni del tipo precedono l'istruzione composta che costituisce il corpo della funzione. La sintassi obsoleta non è aggiornata e non deve essere utilizzata nel nuovo codice. Il codice che utilizza la sintassi obsoleta è, tuttavia, ancora supportato. In questo esempio vengono illustrati i form obsoleti delle dichiarazioni e delle definizioni:

```
double old_style();           /* Obsolete function declaration */

double alt_style( a , real )  /* Obsolete function definition */
    double *real;
    int a;
{
    return ( *real + a ) ;
}
```

Alle funzioni che restituiscono un intero o un puntatore con la stessa dimensione di  `int` non è richiesto di contenere una dichiarazione sebbene l'utilizzo della dichiarazione sia consigliato.

Per la conformità allo standard ANSI C, le dichiarazioni di funzione obsolete con i puntini di sospensione generano ora un errore durante la compilazione con l'opzione /Za e un avviso di livello 4 durante la compilazione con /Ze. Ad esempio:

```cpp
void funct1( a, ... )  /* Generates a warning under /Ze or */
int a;                 /* an error when compiling with /Za */
{
}
```

È necessario riscrivere questa dichiarazione come prototipo:

```cpp
void funct1( int a, ... )
{
}
```

Anche le dichiarazioni di funzione obsolete generano avvisi se, in un secondo momento, si dichiara o si definisce la stessa funzione con i puntini di sospensione o con un parametro con un tipo che non è uguale al relativo tipo promosso.

Nella sezione successiva, [Definizioni di funzioni C](../c-language/c-function-definitions.md), viene illustrata la sintassi per le definizioni di funzioni, inclusa la sintassi obsoleta. Il non terminale per l'elenco dei parametri nella sintassi obsoleta è *identifier-list*.

## <a name="see-also"></a>Vedere anche

[Panoramica delle funzioni](../c-language/overview-of-functions.md)
