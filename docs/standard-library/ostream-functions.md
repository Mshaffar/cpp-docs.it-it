---
title: Funzioni &lt;ostream&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::swap
- ostream/std::endl
- ostream/std::ends
- ostream/std::flush
ms.assetid: d6e56cc0-c8df-4dbe-be10-98e14c35ed3a
caps.latest.revision: "15"
manager: ghogen
helpviewer_keywords:
- std::swap [C++]
- std::endl [C++]
- std::ends [C++]
- std::flush [C++]
ms.openlocfilehash: 9b9f64f67b1649c1c2f3d65f63636fd62601d06a
ms.sourcegitcommit: a7e4956c1150273e8dd39fda8b41655a6cf2cb98
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="ltostreamgt-functions"></a>Funzioni &lt;ostream&gt;

Queste sono le funzioni di modello globale definite in &lt;ostream&gt;. Per le funzioni membro, vedere il [classe basic_ostream](basic-ostream-class.md) documentazione.

||||
|-|-|-|
|[endl](#endl)|[ends](#ends)|[flush](#flush)|
|[swap](#swap)|

## <a name="endl"></a>endl

Termina una riga e scarica il buffer.

```cpp
template class<Elem, Tr> 
basic_ostream<Elem, Tr>& endl(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametri

*Elem*  
Tipo dell'elemento.

*Ostr*  
Un oggetto di tipo **basic_ostream**.

*Tr*  
Tratti di carattere.

### <a name="return-value"></a>Valore restituito

Un oggetto di tipo **basic_ostream**.

### <a name="remarks"></a>Note

Le chiamate manipolatore *Ostr*.[ inserire](../standard-library/basic-ostream-class.md#put)(*Ostr*.[ ampliare](../standard-library/basic-ios-class.md#widen)('\n')), quindi chiama *Ostr*.[ scaricare](../standard-library/basic-ostream-class.md#flush). Restituisce *Ostr*.

### <a name="example"></a>Esempio

```cpp
// ostream_endl.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << endl;
}
```

```Output
testing
```

## <a name="ends"></a>estremità

Termina una stringa.

```cpp
template class<Elem, Tr> 
basic_ostream<Elem, Tr>& ends(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametri

*Elem*  
Tipo dell'elemento.

*Ostr*  
Un oggetto di tipo **basic_ostream**.

*Tr*  
Tratti di carattere.

### <a name="return-value"></a>Valore restituito

Un oggetto di tipo **basic_ostream**.

### <a name="remarks"></a>Note

Le chiamate manipolatore *Ostr*.[ inserire](../standard-library/basic-ostream-class.md#put)(*Elem*('\0')). Restituisce *Ostr*.

### <a name="example"></a>Esempio

```cpp
// ostream_ends.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "a";
   cout << "b" << ends;
   cout << "c" << endl;
}
```

```Output
ab c
```

## <a name="flush"></a>flush

Scarica il buffer.

```cpp
template class<Elem, Tr>
basic_ostream<Elem, Tr>& flush(
   basic_ostream<Elem, Tr>& Ostr);
```

### <a name="parameters"></a>Parametri

*Elem*  
Tipo dell'elemento.

*Ostr*  
Un oggetto di tipo **basic_ostream**.

*Tr*  
Tratti di carattere.

### <a name="return-value"></a>Valore restituito

Un oggetto di tipo **basic_ostream**.

### <a name="remarks"></a>Note

Le chiamate manipolatore *Ostr*.[ scaricare](../standard-library/basic-ostream-class.md#flush). Restituisce *Ostr*.

### <a name="example"></a>Esempio

```cpp
// ostream_flush.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   cout << "testing" << flush;
}
```

```Output
testing
```

## <a name="swap"></a>swap

Scambia i valori di due **basic_ostream** oggetti.

```cpp
template <class Elem, class Tr>
void swap(
   basic_ostream<Elem, Tr>& left,
   basic_ostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Parametri

*Elem*  
Tipo dell'elemento.

*Tr*  
Tratti di carattere.

*left*  
Riferimento lvalue a un **basic_ostream** oggetto.

*right*  
Riferimento lvalue a un **basic_ostream** oggetto.

### <a name="remarks"></a>Note

La funzione di modello **scambio** esegue `left.swap(right)`.

## <a name="see-also"></a>Vedere anche

[\<ostream>](../standard-library/ostream.md)  