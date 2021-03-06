---
title: Overflow del buffer
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 7f9864e6b49446ea68d82e76e877ce9c677b893d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410759"
---
# <a name="buffer-overflow"></a>Overflow del buffer

Dimensioni carattere diverse può causare problemi quando si inserisce i caratteri in un buffer. Si consideri il codice seguente, che copia i caratteri da una stringa, `sz`, in un buffer di `rgch`:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

La domanda è: È stato l'ultimo byte copiati un byte iniziale? Di seguito non risolve il problema perché può provocare un overflow del buffer:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Il `_mbccpy` chiamata tenta di eseguire l'operazione corretta, ovvero copia il carattere completo, se è 1 o 2 byte. Ma non viene preso in considerazione che l'ultimo carattere copiato potrebbe non soddisfare buffer se il carattere wide di 2 byte. La soluzione corretta è:

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Questo codice di verifica overflow del buffer possibile nel ciclo di test, usando `_mbclen` per verificare la dimensione del carattere corrente a cui punta `sz`. Effettuando una chiamata per il `_mbsnbcpy` funzione, è possibile sostituire il codice nel **mentre** ciclo con una singola riga di codice. Ad esempio:

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>Vedere anche

[Suggerimenti sulla programmazione MBCS](../text/mbcs-programming-tips.md)
