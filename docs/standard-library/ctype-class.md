---
title: Classe ctype
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
ms.openlocfilehash: dae6f62a0eda9263986a77b82754596d17be94e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373158"
---
# <a name="ctype-class"></a>Classe ctype

Classe che fornisce un facet utilizzato per classificare i caratteri, eseguire la conversione dalle lettere maiuscole e minuscole, nonché per eseguire la conversione tra il set di caratteri nativi e il set utilizzato dalle impostazioni locali.

## <a name="syntax"></a>Sintassi

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametri

*Chartype*\
Tipo utilizzato all'interno di un programma per codificare i caratteri.

## <a name="remarks"></a>Osservazioni

Come in qualsiasi facet delle impostazioni locali, l'ID dell'oggetto statico ha un valore archiviato iniziale uguale a zero. Il primo tentativo di accedere al valore archiviato consente di archiviare un valore positivo univoco in `id`. I criteri di classificazione vengono forniti come tipo di maschera di bit annidata nella classe base ctype_base.

La libreria standard di C'è definisce due specializzazioni esplicite di questo modello di classe:

- `ctype<char>`, una specializzazione esplicita le cui differenze sono descritte separatamente. Per ulteriori informazioni, vedere [ctype&lt;char&gt; Class](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, che considera gli elementi come caratteri di larghezza.

Altre specializzazioni del `ctype<CharType>`modello di classe :

- Convertire un valore *ch* di tipo *CharType* in `(char)ch`un valore di tipo **char** con expression .

- Convertire un valore *byte* di tipo **char** in un `CharType(byte)`valore di tipo *CharType* con l'espressione .

Tutte le altre operazioni vengono eseguite sui valori **char** `ctype<char>`nello stesso modo della specializzazione esplicita .

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[ctype](#ctype)|Costruttore per gli oggetti della classe `ctype` utilizzati come facet delle impostazioni locali per i caratteri.|

### <a name="typedefs"></a>Typedef

|Nome tipo|Descrizione|
|-|-|
|[char_type](#char_type)|Tipo che descrive un carattere utilizzato dalle impostazioni locali.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[do_is](#do_is)|Funzione virtuale chiamata per verificare se un singolo carattere presenta un attributo specifico oppure per classificare gli attributi di ogni carattere di un intervallo e archiviarli in una matrice.|
|[do_narrow](#do_narrow)|Una funzione virtuale chiamata per `CharType` convertire un carattere di tipo utilizzato dalle impostazioni locali nel carattere corrispondente di tipo **char** nel set di caratteri nativo.|
|[do_scan_is](#do_scan_is)|Funzione virtuale chiamata per individuare il primo carattere di un intervallo che corrisponde a una maschera specificata.|
|[do_scan_not](#do_scan_not)|Funzione virtuale chiamata per individuare il primo carattere di un intervallo che non corrisponde a una maschera specificata.|
|[do_tolower](#do_tolower)|Funzione virtuale chiamata per convertire un carattere o un intervallo di caratteri nelle rispettive lettere minuscole.|
|[do_toupper](#do_toupper)|Funzione virtuale chiamata per convertire un carattere o un intervallo di caratteri in lettere maiuscole.|
|[do_widen](#do_widen)|Una funzione virtuale chiamata per convertire un carattere di tipo **char** `CharType` nel set di caratteri nativo nel carattere corrispondente di tipo utilizzato da un'impostazione locale.|
|[È](#is)|Verifica se un singolo carattere presenta un attributo specifico oppure classifica gli attributi di ogni carattere di un intervallo e li archivia in una matrice.|
|[narrow](#narrow)|Converte un carattere di tipo `CharType` utilizzato dalle impostazioni locali nel carattere corrispondente di tipo char del set di caratteri nativi.|
|[scan_is](#scan_is)|Individua il primo carattere di un intervallo che corrisponde a una maschera specificata.|
|[scan_not](#scan_not)|Individua il primo carattere di un intervallo che non corrisponde a una maschera specificata.|
|[Tolower](#tolower)|Converte un carattere o un intervallo di caratteri in lettere minuscole.|
|[Toupper](#toupper)|Converte un carattere o un intervallo di caratteri in lettere maiuscole.|
|[widen](#widen)|Converte un carattere di tipo **char** nel set `CharType` di caratteri nativo nel carattere corrispondente di tipo utilizzato da un'impostazione locale.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<locale>

**Spazio dei nomi:** std

## <a name="ctypechar_type"></a><a name="char_type"></a>ctype::char_type

Tipo che descrive un carattere utilizzato dalle impostazioni locali.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Osservazioni

Il tipo è un sinonimo del parametro di modello *CharType*.

### <a name="example"></a>Esempio

Vedere la funzione membro [widen](#widen) per un esempio che usa `char_type` come valore restituito.

## <a name="ctypectype"></a><a name="ctype"></a>ctype::ctype

Costruttore per gli oggetti della classe ctype usati come facet delle impostazioni locali per i caratteri.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametri

*_Refs*\
Valore Integer che consente di specificare il tipo di gestione della memoria per l'oggetto.

### <a name="remarks"></a>Osservazioni

I valori possibili per il parametro *_Refs* e il loro significato sono:

- 0: la durata dell'oggetto è gestita dalle impostazioni locali che lo contengono.

- 1: la durata dell'oggetto deve essere gestita manualmente.

- \>1: Questi valori non sono definiti.

Non è possibile fornire esempi diretti, poiché il distruttore è protetto.

Il costruttore `locale::facet` inizializza il relativo oggetto `_Refs`di base con **locale::**[facet](../standard-library/locale-class.md#facet_class)( ).

## <a name="ctypedo_is"></a><a name="do_is"></a>ctype::do_è

Funzione virtuale chiamata per verificare se un singolo carattere presenta un attributo specifico oppure per classificare gli attributi di ogni carattere di un intervallo e archiviarli in una matrice.

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;

virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametri

*maskVal*\
Valore della maschera in base a cui il carattere deve essere sottoposto a test.

*Ch*\
Carattere i cui attributi devono essere sottoposti a test.

*Prima*\
Puntatore al primo carattere dell'intervallo i cui attributi devono essere classificati.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo i cui attributi devono essere classificati.

*Dest*\
Puntatore all'inizio della matrice in cui sono archiviati i valori della maschera che caratterizzano gli attributi di ogni carattere.

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce un valore booleano che è **true** se il carattere sottoposto a test contiene l'attributo descritto dal valore della maschera; **false** se non ha l'attributo.

La seconda funzione membro restituisce una matrice contenente i valori della maschera che caratterizza gli attributi di ogni caratteri dell'intervallo.

### <a name="remarks"></a>Osservazioni

I valori della maschera che classificano gli attributi dei caratteri sono specificati dalla classe [ctype_base](../standard-library/ctype-base-class.md), da cui ctype deriva. La prima funzione membro può accettare espressioni per il primo parametro indicato come maschere di bit e formato dalla combinazione di valori della maschera dagli operatori logici bit per bit (&#124; , & , ^ , ~).

### <a name="example"></a>Esempio

Vedere l'esempio di [is](#is), che chiama `do_is`.

## <a name="ctypedo_narrow"></a><a name="do_narrow"></a>ctype::do_narrow

Una funzione virtuale chiamata per `CharType` convertire un carattere di tipo utilizzato dalle impostazioni locali nel carattere corrispondente di tipo **char** nel set di caratteri nativo.

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;

virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametri

*Ch*\
Carattere di tipo `Chartype` usato dalle impostazioni locali da convertire.

*Predefinito*\
Valore predefinito che deve essere assegnato dalla `CharType` funzione membro ai caratteri di tipo che non dispongono di caratteri di controparte di tipo **char**.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri da convertire.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri da convertire.

*Dest*\
Puntatore const al primo carattere di tipo **char** nell'intervallo di destinazione in cui viene archiviato l'intervallo di caratteri convertito.

### <a name="return-value"></a>Valore restituito

La prima funzione membro protetta restituisce il carattere nativo `CharType` di tipo char che corrisponde al carattere del parametro di tipo o *default* se non è definita alcuna controparte.

La seconda funzione membro protetto restituisce un puntatore per l'intervallo di destinazione di caratteri nativi convertiti a partire da caratteri di tipo `CharType`.

### <a name="remarks"></a>Osservazioni

La seconda funzione modello `dest`membro `I`protetta `do_narrow` `first` archivia `default`in `I` [ ] il `last`  -  `first`valore ( [ `I`], ), per nell'intervallo [0, ).

### <a name="example"></a>Esempio

Vedere l'esempio di [narrow](#narrow), che chiama `do_narrow`.

## <a name="ctypedo_scan_is"></a><a name="do_scan_is"></a>ctype::do_scan_is

Funzione virtuale chiamata per individuare il primo carattere di un intervallo che corrisponde a una maschera specificata.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*maskVal*\
Valore della maschera da confrontare per carattere.

*Prima*\
Puntatore al primo carattere nell'intervallo da analizzare.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo da analizzare.

### <a name="return-value"></a>Valore restituito

Puntatore al primo carattere in un intervallo che corrisponde a una maschera specificata. Se tale valore non esiste, la funzione restituisce *last*.

### <a name="remarks"></a>Osservazioni

La funzione membro protetta `ptr` restituisce `first`il `last`puntatore più `maskVal` \* `ptr`piccolo nell'intervallo [ , ) per il quale [do_is](#do_is)( , ) è true.

### <a name="example"></a>Esempio

Vedere l'esempio di [scan_is](#scan_is), che chiama `do_scan_is`.

## <a name="ctypedo_scan_not"></a><a name="do_scan_not"></a>ctype::do_scan_not

Funzione virtuale chiamata per individuare il primo carattere di un intervallo che non corrisponde a una maschera specificata.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*maskVal*\
Valore della maschera che non deve essere confrontata per carattere.

*Prima*\
Puntatore al primo carattere nell'intervallo da analizzare.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo da analizzare.

### <a name="return-value"></a>Valore restituito

Puntatore al primo carattere in un intervallo che non corrisponde a una maschera specificata. Se tale valore non esiste, la funzione restituisce *last*.

### <a name="remarks"></a>Osservazioni

La funzione membro protetta `ptr` restituisce `first`il `last`puntatore più `maskVal` \* `ptr`piccolo nell'intervallo [ , ) per il quale [do_is](#do_is)( , ) è false.

### <a name="example"></a>Esempio

Vedere l'esempio di [scan_not](#scan_not), che chiama `do_scan_not`.

## <a name="ctypedo_tolower"></a><a name="do_tolower"></a>ctype::do_tolower

Funzione virtuale chiamata per convertire un carattere o un intervallo di caratteri in lettere minuscole.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Ch*\
Carattere da convertire in lettere minuscole.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

### <a name="return-value"></a>Valore restituito

La prima funzione membro protetta restituisce la forma minuscola del parametro *ch*. Se non esiste alcuna forma minuscola, restituisce *ch*. La seconda funzione membro protetta restituisce *last*.

### <a name="remarks"></a>Osservazioni

La seconda funzione del modello `first` membro `I`protetto `I` sostituisce ogni elemento `last`  -  `first`[ `do_tolower` `first` ], per nell'intervallo [0, ] con ( [ `I`]).

### <a name="example"></a>Esempio

Vedere l'esempio di [tolower](#tolower) che chiama `do_tolower`.

## <a name="ctypedo_toupper"></a><a name="do_toupper"></a>ctype::do_toupper

Funzione virtuale chiamata per convertire un carattere o un intervallo di caratteri in lettere maiuscole.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Ch*\
Carattere da convertire in lettere maiuscole.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

### <a name="return-value"></a>Valore restituito

La prima funzione membro protetta restituisce la forma maiuscola del parametro *ch*. Se non esiste alcuna forma maiuscola, restituisce *ch*. La seconda funzione membro protetta restituisce *last*.

### <a name="remarks"></a>Osservazioni

La seconda funzione del modello `first` membro `I`protetto `I` sostituisce ogni elemento `last`  -  `first`[ `do_toupper` `first` ], per nell'intervallo [0, ] con ( [ `I`]).

### <a name="example"></a>Esempio

Vedere l'esempio di [toupper](#toupper) che chiama `do_toupper`.

## <a name="ctypedo_widen"></a><a name="do_widen"></a>ctype::do_widen

Una funzione virtuale chiamata per convertire un carattere di tipo **char** `CharType` nel set di caratteri nativo nel carattere corrispondente di tipo utilizzato da un'impostazione locale.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametri

*byte*\
Carattere di tipo **char** nel set di caratteri nativo da convertire.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri da convertire.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri da convertire.

*Dest*\
Puntatore al primo carattere di tipo `CharType` nell'intervallo di destinazione che archivia l'intervallo di caratteri convertito.

### <a name="return-value"></a>Valore restituito

La prima funzione membro protetta `CharType` restituisce il carattere di tipo che corrisponde al carattere del parametro di tipo nativo **char**.

La seconda funzione membro protetta restituisce un `CharType` puntatore all'intervallo di caratteri di destinazione di tipo utilizzato dalle impostazioni locali convertite da caratteri nativi di tipo **char**.

### <a name="remarks"></a>Osservazioni

La seconda funzione del modello membro protetto archivia in `dest`[ `I`] il valore `do_widen`( `first` [ `I`]), per `I` nell'intervallo [0, `last` - `first`).

### <a name="example"></a>Esempio

Vedere l'esempio di [widen](#widen), che chiama `do_widen`.

## <a name="ctypeis"></a><a name="is"></a>ctype::is

Verifica se un singolo carattere presenta un attributo specifico oppure classifica gli attributi di ogni carattere di un intervallo e li archivia in una matrice.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametri

*maskVal*\
Valore della maschera in base a cui il carattere deve essere sottoposto a test.

*Ch*\
Carattere i cui attributi devono essere sottoposti a test.

*Prima*\
Puntatore al primo carattere dell'intervallo i cui attributi devono essere classificati.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo i cui attributi devono essere classificati.

*Dest*\
Puntatore all'inizio della matrice in cui sono archiviati i valori della maschera che caratterizzano gli attributi di ogni carattere.

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce **true** se il carattere testato ha l'attributo descritto dal valore della maschera; **false** se non riesce ad avere l'attributo.

La seconda funzione membro restituisce un puntatore all'ultimo carattere dell'intervallo i cui attributi devono essere classificati.

### <a name="remarks"></a>Osservazioni

I valori della maschera che classificano gli attributi dei caratteri sono specificati dalla classe [ctype_base](../standard-library/ctype-base-class.md), da cui deriva ctype. La prima funzione membro può accettare espressioni per il primo parametro indicato come maschere di bit e formato dalla combinazione di valori della maschera dagli operatori logici bit per bit (&#124; , & , ^ , ~).

### <a name="example"></a>Esempio

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="ctypenarrow"></a><a name="narrow"></a>ctype::narrow

Converte i `CharType` caratteri di tipo utilizzato da un'impostazione locale nei caratteri corrispondenti di tipo **char** nel set di caratteri nativo.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametri

*Ch*\
Carattere di tipo `Chartype` usato dalle impostazioni locali da convertire.

*Predefinito*\
Valore predefinito che deve essere assegnato dalla `CharType` funzione membro ai caratteri di tipo che non dispongono di caratteri di controparte di tipo **char**.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri da convertire.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri da convertire.

*Dest*\
Puntatore const al primo carattere di tipo **char** nell'intervallo di destinazione in cui viene archiviato l'intervallo di caratteri convertito.

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce **char** il carattere nativo di `CharType default` tipo char che corrisponde al carattere del parametro di tipo se non è definita la controparte.

La seconda funzione membro restituisce un puntatore per l'intervallo di destinazione di caratteri nativi convertiti a partire da caratteri di tipo `CharType`.

### <a name="remarks"></a>Osservazioni

La prima funzione membro`ch` `default`restituisce [do_narrow](#do_narrow)( , ). La seconda funzione membro`first` `last`restituisce `dest` [do_narrow](#do_narrow) ( , , `default`, ). Solo i caratteri d'origine di base hanno definitivamente un'immagine inversa univoca `CharType` in `narrow`. Per questi caratteri d'origine di base, l'invariabile seguente include: `narrow` ( [widen](#widen) ( **c** ), 0 ) == **c**.

### <a name="example"></a>Esempio

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="ctypescan_is"></a><a name="scan_is"></a>ctype::scan_is

Individua il primo carattere di un intervallo che corrisponde a una maschera specificata.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*maskVal*\
Valore della maschera da confrontare per carattere.

*Prima*\
Puntatore al primo carattere nell'intervallo da analizzare.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo da analizzare.

### <a name="return-value"></a>Valore restituito

Puntatore al primo carattere in un intervallo che corrisponde a una maschera specificata. Se tale valore non esiste, la funzione restituisce *last*.

### <a name="remarks"></a>Osservazioni

La funzione membro`maskVal`restituisce `last` [do_scan_is](#do_scan_is)( , `first`, ).

### <a name="example"></a>Esempio

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="ctypescan_not"></a><a name="scan_not"></a>ctype::scan_not

Individua il primo carattere di un intervallo che non corrisponde a una maschera specificata.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*maskVal*\
Valore della maschera che non deve essere confrontata per carattere.

*Prima*\
Puntatore al primo carattere nell'intervallo da analizzare.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo da analizzare.

### <a name="return-value"></a>Valore restituito

Puntatore al primo carattere in un intervallo che non corrisponde a una maschera specificata. Se tale valore non esiste, la funzione restituisce *last*.

### <a name="remarks"></a>Osservazioni

La funzione membro`maskVal`restituisce `last` [do_scan_not](#do_scan_not)( , `first`, ).

### <a name="example"></a>Esempio

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="ctypetolower"></a><a name="tolower"></a>ctype::tolower

Converte un carattere o un intervallo di caratteri in lettere minuscole.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Ch*\
Carattere da convertire in lettere minuscole.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce la forma minuscola del parametro *ch*. Se non esiste alcuna forma minuscola, restituisce *ch*.

La seconda funzione membro restituisce *l'ultima*funzione .

### <a name="remarks"></a>Osservazioni

La prima funzione [do_tolower](#do_tolower)membro`ch`restituisce do_tolower ( ). La seconda funzione membro`first` `last`restituisce [do_tolower](#do_tolower)( , ).

### <a name="example"></a>Esempio

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="ctypetoupper"></a><a name="toupper"></a>ctype::toupper

Converte un carattere o un intervallo di caratteri in lettere maiuscole.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Ch*\
Carattere da convertire in lettere maiuscole.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri di cui deve essere convertita la combinazione di maiuscole/minuscole.

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce la forma maiuscola del parametro *ch*. Se non esiste alcuna forma maiuscola, restituisce *ch*.

La seconda funzione membro restituisce *l'ultima*funzione .

### <a name="remarks"></a>Osservazioni

La prima funzione [do_toupper](#do_toupper)membro`ch`restituisce do_toupper ( ). La seconda funzione membro `first` `last`restituisce [do_toupper](#do_toupper)( , ).

### <a name="example"></a>Esempio

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="ctypewiden"></a><a name="widen"></a>ctype::widen

Converte un carattere di tipo **char** nel set `CharType` di caratteri nativo nel carattere corrispondente di tipo utilizzato da un'impostazione locale.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametri

*byte*\
Carattere di tipo char nel set di caratteri nativo da convertire.

*Prima*\
Puntatore al primo carattere in un intervallo di caratteri da convertire.

*Ultima*\
Puntatore al carattere immediatamente successivo all'ultimo carattere dell'intervallo dei caratteri da convertire.

*Dest*\
Puntatore al primo carattere di tipo `CharType` nell'intervallo di destinazione che archivia l'intervallo di caratteri convertito.

### <a name="return-value"></a>Valore restituito

La prima funzione membro restituisce il carattere di tipo `CharType` che corrisponde al carattere del parametro di tipo nativo **char**.

La seconda funzione membro restituisce un puntatore `CharType` all'intervallo di caratteri di destinazione di tipo utilizzato dalle impostazioni locali convertite da caratteri nativi di tipo **char**.

### <a name="remarks"></a>Osservazioni

La prima funzione [do_widen](#do_widen)membro`byte`restituisce do_widen ( ). La seconda funzione membro`first` `last`restituisce `dest` [do_widen](#do_widen)( , , ). ).

### <a name="example"></a>Esempio

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>Vedere anche

[\<>delle impostazioni locali](../standard-library/locale.md)\
[Sicurezza dei filettatura nella libreria standard di C](../standard-library/thread-safety-in-the-cpp-standard-library.md)
