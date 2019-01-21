---
title: Classe HString
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 800ed98656493efc3e0ce59739dab7e4c0bc681f
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336628"
---
# <a name="hstring-class"></a>Classe HString

Classe helper per la gestione della durata di un' [HSTRING](/windows/desktop/WinRT/hstring) adottando il modello RAII.

## <a name="syntax"></a>Sintassi

```cpp
class HString;
```

## <a name="remarks"></a>Note

Il Runtime di Windows fornisce l'accesso alle stringhe attraverso [HSTRING](/windows/desktop/WinRT/hstring) gli handle. Il `HString` classe fornisce funzioni comode e operatori per semplificare l'uso di handle di HSTRING. Questa classe può gestire la durata della sua proprietà tramite un modello RAII HSTRING.

## <a name="members"></a>Membri

### <a name="public-constructors"></a>Costruttori pubblici

Nome                                | Descrizione
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Inizializza una nuova istanza della classe `HString`.
[HString::~HString](#tilde-hstring) | Elimina l'istanza corrente del `HString` classe.

### <a name="public-methods"></a>Metodi pubblici

Nome                                     | Descrizione
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | Associa l'oggetto specificato `HString` oggetto con l'attuale `HString` oggetto.
[HString::CopyTo](#copyto)               | Copia l'oggetto corrente `HString` oggetto in un oggetto HSTRING.
[HString::Detach](#detach)               | Disassocia i `HString` oggetto dal relativo valore sottostante.
[HString::Get](#get)                     | Recupera il valore di handle sottostante di HSTRING.
[HString::GetAddressOf](#getaddressof)   | Recupera un puntatore all'handle sottostante di HSTRING.
[HString::IsValid](#isvalid)             | Indica se l'oggetto corrente `HString` oggetto è valido.
[HString::MakeReference](#makereference) | Crea un `HStringReference` oggetto da un parametro di stringa specificata.
[HString::Release](#release)             | Elimina il valore string sottostante e inizializza l'oggetto corrente `HString` oggetto su un valore vuoto.
[HString::Set](#set)                     | Imposta il valore dell'oggetto corrente `HString` oggetto per la stringa di caratteri wide specificata o `HString` parametro.

### <a name="public-operators"></a>Operatori pubblici

Nome                                         | Descrizione
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | Sposta il valore di un'altra `HString` oggetto all'oggetto corrente `HString` oggetto.
[HString::operator==](#operator-equality)    | Indica se i due parametri sono uguali.
[HString::operator!=](#operator-inequality)  | Indica se i due parametri non sono uguali.
[HString::operator&lt;](#operator-less-than) | Indica se il primo parametro è minore di secondo parametro.

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`HString`

## <a name="requirements"></a>Requisiti

**Intestazione:** corewrappers. h

**Spazio dei nomi:** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString::~HString

Elimina l'istanza corrente del `HString` classe.

```cpp
~HString() throw()
```

## <a name="attach"></a>HString::Attach

Associa l'oggetto specificato `HString` oggetto con l'attuale `HString` oggetto.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parametri

*hstr*<br/>
Oggetto `HString` esistente.

## <a name="copyto"></a>HString::CopyTo

Copia l'oggetto corrente `HString` oggetto in un oggetto HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametri

*str*<br/>
HSTRING che riceve la copia.

### <a name="remarks"></a>Note

Questo metodo chiama il [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) (funzione).

## <a name="detach"></a>HString::Detach

Disassocia i `HString` oggetto dal relativo valore sottostante.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Valore restituito

Sottostante `HString` valore prima dell'operazione di scollegamento avviato.

## <a name="get"></a>HString::Get

Recupera il valore di handle sottostante di HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Valore restituito

Il valore di handle sottostante di HSTRING

## <a name="getaddressof"></a>HString::GetAddressOf

Recupera un puntatore all'handle sottostante di HSTRING.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Valore restituito

Puntatore a handle sottostante di HSTRING.

### <a name="remarks"></a>Note

Dopo questa operazione, viene eliminato il valore di stringa dell'handle sottostante di HSTRING.

## <a name="hstring"></a>HString::HString

Inizializza una nuova istanza della classe `HString`.

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parametri

*hstr*<br/>
Un handle HSTRING.

*other*<br/>
Oggetto `HString` esistente.

### <a name="remarks"></a>Note

Il primo costruttore inizializza un nuovo `HString` oggetto che è vuota.

Il secondo costruttore inizializza un nuovo `HString` oggetto sul valore dell'oggetto esistente *altri* parametro e quindi distrugge il *altri* parametro.

## <a name="isvalid"></a>HString::IsValid

Indica se l'oggetto corrente `HString` oggetto è vuoto o meno.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parametri

**true** se l'oggetto corrente `HString` oggetto non è vuoto; in caso contrario, **false**.

## <a name="makereference"></a>HString::MakeReference

Crea un `HStringReference` oggetto da un parametro di stringa specificata.

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Parametri

*sizeDest*<br/>
Un parametro di modello che specifica le dimensioni della destinazione `HStringReference` buffer.

*str*<br/>
Un riferimento a una stringa di caratteri "wide".

*len*<br/>
La lunghezza massima del *str* buffer del parametro da utilizzare in questa operazione. Se il *len* parametro non è specificato, l'intera *str* parametro viene utilizzato.

### <a name="return-value"></a>Valore restituito

Un' `HStringReference` il cui valore è identico a quello di specificato *str* parametro.

## <a name="operator-assign"></a>Operatore hstring:: Operator =

Sposta il valore di un'altra `HString` oggetto all'oggetto corrente `HString` oggetto.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parametri

*other*<br/>
Oggetto `HString` esistente.

### <a name="remarks"></a>Note

Il valore dell'oggetto esistente *altri* viene copiato l'oggetto corrente `HString` oggetto e quindi la *altri* oggetto viene eliminato definitivamente.

## <a name="operator-equality"></a>Operatore hstring:: Operator = =

Indica se i due parametri sono uguali.

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametri

*lhs*<br/>
Il primo parametro da confrontare. *LHS* può essere un `HString` o `HStringReference` oggetto o un handle HSTRING.

*rhs*<br/>
Il secondo parametro da confrontare. *rhs* può essere un' `HString` o `HStringReference` oggetto o un handle HSTRING.

### <a name="return-value"></a>Valore restituito

**true** se il *lhs* e *rhs* parametri sono uguali; in caso contrario, **false**.

## <a name="operator-inequality"></a>Hstring:: operator! = (operatore)

Indica se i due parametri non sono uguali.

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametri

*lhs*<br/>
Il primo parametro da confrontare. *LHS* può essere un `HString` o `HStringReference` oggetto o un handle HSTRING.

*rhs*<br/>
Il secondo parametro da confrontare. *rhs* può essere un' `HString` o `HStringReference` oggetto o un handle HSTRING.

### <a name="return-value"></a>Valore restituito

**true** se il *lhs* e *rhs* parametri non sono uguali; in caso contrario, **false**.

## <a name="operator-less-than"></a>Operatore hstring::&lt; operatore

Indica se il primo parametro è minore di secondo parametro.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parametri

*lhs*<br/>
Il primo parametro da confrontare. *LHS* può essere un riferimento a un `HString`.

*rhs*<br/>
Il secondo parametro da confrontare. *rhs* può essere un riferimento a un `HString`.

### <a name="return-value"></a>Valore restituito

**true** se il *lhs* parametro è minore del *rhs* parametro; in caso contrario, **false**.

## <a name="release"></a>HString::Release

Elimina il valore string sottostante e inizializza l'oggetto corrente `HString` oggetto su un valore vuoto.

```cpp
void Release() throw()
```

## <a name="set"></a>HString::Set

Imposta il valore dell'oggetto corrente `HString` oggetto per la stringa di caratteri wide specificata o `HString` parametro.

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Parametri

*str*<br/>
Una stringa di caratteri "wide".

*len*<br/>
La lunghezza massima del *str* parametro assegnato all'oggetto corrente `HString` oggetto.

*hstr*<br/>
Oggetto `HString` esistente.