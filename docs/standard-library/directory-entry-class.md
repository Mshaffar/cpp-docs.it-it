---
title: Classe directory_entry
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458965"
---
# <a name="directoryentry-class"></a>Classe directory_entry

Descrive un oggetto restituito da `*X`, dove *X* è una classe [directory_iterator](../standard-library/directory-iterator-class.md) o [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md).

## <a name="syntax"></a>Sintassi

```cpp
class directory_entry;
```

## <a name="remarks"></a>Note

La classe archivia un oggetto di tipo [path](../standard-library/path-class.md). Il tipo `path` archiviato può essere un'istanza della [classe path](../standard-library/path-class.md) o del tipo derivato da `path`. Archivia anche due valori [file_type](../standard-library/filesystem-enumerations.md#file_type). Uno rappresenta ciò che si conosce sullo stato del nome file archiviato e uno rappresenta ciò che si conosce sullo stato del collegamento simbolico del nome file.

Per altre informazioni ed esempi di codice, vedere [File System Navigation (C++)](../standard-library/file-system-navigation.md) (Esplorazione del file system (C++)).

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[directory_entry](#directory_entry)|I costruttori impostati come predefiniti si comportano come previsto. Il quarto costruttore inizializza `mypath` *pval* `mystat` , *stat_arg*e `mysymstat` *symstat_arg*.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[assign](#assign)|La funzione membro assegna *pval* a `mypath`, *Stat* a `mystat`e *symstat* a `mysymstat`.|
|[path](#path)|La funzione membro restituisce `mypath`.|
|[replace_filename](#replace_filename)|La funzione membro sostituisce `mypath` con `mypath.parent_path()`  /  *pval* ,`mystat` con *stat_arg* e`mysymstat` con *symstat_arg*|
|[status](#status)|Entrambe le funzioni membro `mystat` restituiscono probabilmente prima modificate.|
|[symlink_status](#symlink_status)|Entrambe le funzioni membro `mysymstat` restituiscono probabilmente prima modificate.|

### <a name="operators"></a>Operatori

|Operator|DESCRIZIONE|
|-|-|
|[operator!=](#op_neq)|Sostituisce gli elementi dell'elenco con una copia di un altro elenco.|
|[operator=](#op_as)|Gli operatori di assegnazione membro impostati come predefiniti si comportano come previsto.|
|[operator==](#op_eq)|Restituisce `mypath == right.mypath`.|
|[operator<](#op_lt)|Restituisce `mypath < right.mypath`.|
|[operator<=](#op_lteq)|Restituisce `!(right < *this)`.|
|[operator>](#op_gt)|Restituisce `right < *this`.|
|[operator>=](#op_gteq)|Restituisce `!(*this < right)`.|
|[operatore const path_type &](#path_type)|Restituisce `mypath`.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<Experimental/filesystem&gt;

**Spazio nomi:** std::experimental::filesystem

## <a name="assign"></a>assegnare

La funzione membro assegna *pval* a `mypath`, *stat_arg* a `mystat`e *symstat_arg* a `mysymstat`.

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametri

*Pval*\
Percorso del nome file archiviato.

*stat_arg*\
Stato del nome file archiviato.

*symstat_arg*\
Stato del collegamento simbolico del nome file archiviato.

## <a name="directory_entry"></a>directory_entry

I costruttori impostati come predefiniti si comportano come previsto. Il quarto costruttore inizializza `mypath` *pval* `mystat` , *stat_arg*e `mysymstat` *symstat_arg*.

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametri

*Pval*\
Percorso del nome file archiviato.

*stat_arg*\
Stato del nome file archiviato.

*symstat_arg*\
Stato del collegamento simbolico del nome file archiviato.

## <a name="op_neq"></a>operatore! =

La funzione membro restituisce `!(*this == right)`.

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametri

*Ok*\
[Directory_entry](../standard-library/directory-entry-class.md) da confrontare con `directory_entry`.

## <a name="op_as"></a> operator=

Gli operatori di assegnazione membro impostati come predefiniti si comportano come previsto.

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>Parametri

*Ok*\
[Directory_entry](../standard-library/directory-entry-class.md) copiato nell'oggetto `directory_entry`.

## <a name="op_eq"></a> operator==

La funzione membro restituisce `mypath == right.mypath`.

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametri

*Ok*\
[Directory_entry](../standard-library/directory-entry-class.md) da confrontare con `directory_entry`.

## <a name="op_lt"></a> Operatore&lt;

La funzione membro restituisce `mypath < right.mypath`.

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametri

*Ok*\
[Directory_entry](../standard-library/directory-entry-class.md) da confrontare con `directory_entry`.

## <a name="op_lteq"></a>operatore&lt;=

La funzione membro restituisce `!(right < *this)`.

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametri

*Ok*\
[Directory_entry](../standard-library/directory-entry-class.md) da confrontare con `directory_entry`.

## <a name="op_gt"></a> Operatore&gt;

La funzione membro restituisce `right < *this`.

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametri

*Ok*\
[Directory_entry](../standard-library/directory-entry-class.md) da confrontare con `directory_entry`.

## <a name="op_gteq"></a>operatore&gt;=

La funzione membro restituisce `!(*this < right)`.

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>Parametri

*Ok*\
[Directory_entry](../standard-library/directory-entry-class.md) da confrontare con `directory_entry`.

## <a name="path_type"></a>operatore const path_type &

L'operatore membro restituisce `mypath`.

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>percorso

La funzione membro restituisce `mypath`.

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

La funzione membro sostituisce `mypath` con `mypath.parent_path()`  /  *pval* ,`mystat` con *stat_arg* e`mysymstat` con *symstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>Parametri

*Pval*\
Percorso del nome file archiviato.

*stat_arg*\
Stato del nome file archiviato.

*symstat_arg*\
Stato del collegamento simbolico del nome file archiviato.

## <a name="status"></a>stato

Entrambe le funzioni membro `mystat` restituiscono probabilmente prima modificate nel modo seguente:

1. Se `status_known(mystat)` non eseguire alcuna operazione.

1. In caso contrario `!status_known(mysymstat) && !is_symlink(mysymstat)` , `mystat = mysymstat`se quindi.

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametri

*EC*\
Codice di errore dello stato.

## <a name="symlink_status"></a>symlink_status

Entrambe le funzioni membro `mysymstat` restituiscono probabilmente prima modificate nel modo seguente: Se `status_known(mysymstat)` non eseguire alcuna operazione. In caso contrario, `mysymstat = symlink_status(mypval)`.

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>Parametri

*EC*\
Codice di errore dello stato.

## <a name="see-also"></a>Vedere anche

[Riferimento file di intestazione](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem&gt;](../standard-library/filesystem.md)
