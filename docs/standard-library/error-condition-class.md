---
title: Classe error_condition
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
ms.openlocfilehash: cbadf6a22871cc9a23d37c095a398490c8a4c72c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245792"
---
# <a name="errorcondition-class"></a>Classe error_condition

Rappresenta i codici di errore definiti dall'utente.

## <a name="syntax"></a>Sintassi

```cpp
class error_condition;
```

## <a name="remarks"></a>Note

Un oggetto di tipo `error_condition` archivia un valore di codice di errore e un puntatore a un oggetto che rappresenta una [categoria](../standard-library/error-category-class.md) di codici di errore usati per gli errori definiti dall'utente segnalati.

## <a name="members"></a>Members

### <a name="constructors"></a>Costruttori

|||
|-|-|
|[error_condition](#error_condition)|Costruisce un oggetto di tipo `error_condition`.|

### <a name="typedefs"></a>Definizioni typedef

|||
|-|-|
|[value_type](#value_type)|Tipo che rappresenta il valore del codice di errore archiviato.|

### <a name="functions"></a>Funzioni

|||
|-|-|
|[assign](#assign)|Assegna un valore di codice di errore e una categoria a una condizione di errore.|
|[category](#category)|Restituisce la categoria dell'errore.|
|[clear](#clear)|Cancella il valore del codice di errore e la categoria.|
|[message](#message)|Restituisce il nome del codice di errore.|

### <a name="operators"></a>Operatori

|||
|-|-|
|[operator==](#op_eq_eq)|Verifica l'uguaglianza tra oggetti `error_condition`.|
|[operator!=](#op_neq)|Verifica la disuguaglianza tra oggetti `error_condition`.|
|[operator<](#op_lt)|Verifica se l'oggetto `error_condition` è più piccolo dell'oggetto `error_code` passato per il confronto.|
|[operator=](#op_eq)|Assegna un nuovo valore di enumerazione all'oggetto `error_condition`.|
|[operator bool](#op_bool)|Crea una variabile di tipo `error_condition`.|

### <a name="assign"></a> assegnare

Assegna un valore di codice di errore e una categoria a una condizione di errore.

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>Parametri

*Val*\
Il valore del codice di errore da archiviare nell'`error_code`.

*Servizio*\
La categoria dell'errore da archiviare nell'`error_code`.

#### <a name="remarks"></a>Note

La funzione membro Archivia *val* come valore del codice di errore e un puntatore a *servizio*.

### <a name="category"></a> Categoria

Restituisce la categoria dell'errore.

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>Valore restituito

Riferimento alla categoria dell'errore archiviato

#### <a name="remarks"></a>Note

### <a name="clear"></a> Cancella

Cancella il valore del codice di errore e la categoria.

```cpp
clear();
```

#### <a name="remarks"></a>Note

La funzione membro archivia un valore del codice di errore zero e un puntatore all'oggetto [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="error_condition"></a> error_condition

Costruisce un oggetto di tipo `error_condition`.

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>Parametri

*Val*\
Il valore del codice di errore da archiviare nell'`error_condition`.

*Servizio*\
La categoria dell'errore da archiviare nell'`error_condition`.

*_Errcode*\
Il valore di enumerazione da archiviare nell'`error_condition`.

#### <a name="remarks"></a>Note

Il primo costruttore archivia un valore del codice di errore zero e un puntatore alla [generic_category](../standard-library/system-error-functions.md#generic_category).

Il secondo costruttore Archivia *val* come valore del codice di errore e un puntatore a [error_category](../standard-library/error-category-class.md).

Il terzo costruttore archivia `(value_type)_Errcode` come valore del codice di errore e un puntatore alla [generic_category](../standard-library/system-error-functions.md#generic_category).

### <a name="message"></a> Messaggio

Restituisce il nome del codice di errore.

```cpp
string message() const;
```

#### <a name="return-value"></a>Valore restituito

`string` che rappresenta il nome del codice di errore.

#### <a name="remarks"></a>Note

Questa funzione membro restituisce `category().message(value())`.

### <a name="op_eq_eq"></a> operator==

Verifica l'uguaglianza tra oggetti `error_condition`.

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametri

*Ok*\
L'oggetto di cui verificare l'uguaglianza.

#### <a name="return-value"></a>Valore restituito

**true** se gli oggetti sono uguali; in caso contrario, **false**.

#### <a name="remarks"></a>Note

L'operatore membro restituisce `category() == right.category() && value == right.value()`.

### <a name="op_neq"></a> operatore! =

Verifica la disuguaglianza tra oggetti `error_condition`.

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametri

*Ok*\
Oggetto di cui verificare la disuguaglianza.

#### <a name="return-value"></a>Valore restituito

**true** se il `error_condition` non è uguale all'oggetto il `error_condition` oggetto passato in *a destra*; in caso contrario **false**.

#### <a name="remarks"></a>Note

L'operatore membro restituisce `!(*this == right)`.

### <a name="op_lt"></a> Operatore&lt;

Verifica se l'oggetto `error_condition` è più piccolo dell'oggetto `error_code` passato per il confronto.

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>Parametri

*Ok*\
L'oggetto `error_condition` da confrontare.

#### <a name="return-value"></a>Valore restituito

**true** se l'oggetto `error_condition` è più piccolo dell'oggetto `error_condition` passato per il confronto; in caso contrario **false**.

#### <a name="remarks"></a>Note

L'operatore membro restituisce `category() < right.category() || category() == right.category() && value < right.value()`.

### <a name="op_eq"></a> operator=

Assegna un nuovo valore di enumerazione all'oggetto `error_condition`.

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

#### <a name="parameters"></a>Parametri

*_Errcode*\
Il valore di enumerazione da assegnare all'oggetto `error_condition`.

#### <a name="return-value"></a>Valore restituito

Un riferimento all'oggetto `error_condition` a cui viene assegnato il nuovo valore di enumerazione dalla funzione membro.

#### <a name="remarks"></a>Note

L'operatore membro archivia `(value_type)error` come valore del codice di errore e un puntatore alla [generic_category](../standard-library/system-error-functions.md#generic_category). Restituisce `*this`.

### <a name="op_bool"></a> operator bool

Crea una variabile di tipo `error_condition`.

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>Valore restituito

Il valore booleano dell'oggetto `error_condition`.

#### <a name="remarks"></a>Note

L'operatore restituisce un valore convertibile in **true** solo se [valore](#value) non è uguale a zero. Il tipo restituito è convertibile solo in **bool**, non in `void *` o altri tipi scalari noti.

### <a name="value"></a> Valore

Restituisce il valore del codice di errore archiviato.

```cpp
value_type value() const;
```

#### <a name="return-value"></a>Valore restituito

Il valore del codice di errore archiviato di tipo [value_type](#value_type).

#### <a name="remarks"></a>Note

### <a name="value_type"></a> value_type

Tipo che rappresenta il valore del codice di errore archiviato.

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Note

La definizione del tipo è un sinonimo **int**.
