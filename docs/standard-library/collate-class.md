---
title: Classe collate
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: f05c2e9482f8a0bada3868fdc946d4d26a0e0e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371929"
---
# <a name="collate-class"></a>Classe collate

Modello di classe che descrive un oggetto che può essere utilizzato come facet delle impostazioni locali per controllare l'ordinamento e il raggruppamento di caratteri all'interno di una stringa, i confronti tra di essi e l'hashing delle stringhe.

## <a name="syntax"></a>Sintassi

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametri

*Chartype*\
Tipo utilizzato all'interno di un programma per codificare i caratteri.

## <a name="remarks"></a>Osservazioni

Come in qualsiasi facet delle impostazioni locali, l'ID dell'oggetto statico ha un valore archiviato iniziale uguale a zero. Il primo tentativo di accedere al valore archiviato consente di archiviare un valore positivo univoco in `id`. In alcuni linguaggi i caratteri vengono raggruppati e considerati come singoli caratteri, mentre in altri linguaggi i singoli caratteri vengono considerati come se fossero due caratteri. I servizi di ordinamento forniti dalla classe di ordinamento forniscono una modalità di ordinamento per questi casi.

### <a name="constructors"></a>Costruttori

|Costruttore|Descrizione|
|-|-|
|[Collate](#collate)|Costruttore per gli oggetti della classe `collate` utilizzato come facet delle impostazioni locali per gestire le convenzioni di ordinamento delle stringhe.|

### <a name="typedefs"></a>Typedef

|Nome tipo|Descrizione|
|-|-|
|[char_type](#char_type)|Tipo che descrive un carattere di tipo `CharType`.|
|[string_type](#string_type)|Tipo che descrive una stringa di tipo `basic_string` contenente caratteri di tipo `CharType`.|

### <a name="member-functions"></a>Funzioni membro

|Funzione membro|Descrizione|
|-|-|
|[Confrontare](#compare)|Confronta due sequenze di caratteri in base alle regole specifiche del relativo facet per verificarne l'uguaglianza o la disuguaglianza.|
|[do_compare](#do_compare)|Funzione virtuale chiamata per confrontare due sequenze di caratteri in base alle regole specifiche del relativo facet per verificarne l'uguaglianza o la disuguaglianza.|
|[do_hash](#do_hash)|Funzione virtuale chiamata per determinare il valore hash delle sequenze in base alle regole specifiche del relativo facet.|
|[do_transform](#do_transform)|Funzione virtuale chiamata per convertire una sequenza di caratteri in una stringa che può essere utilizzata nei confronti lessicografici con altre sequenze di caratteri convertite in modo analogo dalle stesse impostazioni locali.|
|[Hash](#hash)|Determina il valore hash della sequenza in base alle regole specifiche del relativo facet.|
|[Trasformare](#transform)|Converte una sequenza di caratteri dalle impostazioni locali in una stringa che può essere utilizzata nei confronti lessicografici con altre sequenze di caratteri convertite in modo analogo dalle stesse impostazioni locali.|

## <a name="requirements"></a>Requisiti

**Intestazione:** \<locale>

**Spazio dei nomi:** std

## <a name="collatechar_type"></a><a name="char_type"></a>fascicola::char_type

Tipo che descrive un carattere di tipo `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Osservazioni

Il tipo è un sinonimo del parametro di modello `CharType`.

## <a name="collatecollate"></a><a name="collate"></a>fascicolare::fascicolare

Costruttore per gli oggetti della classe collate usato come facet delle impostazioni locali per gestire le convenzioni di ordinamento delle stringhe.

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametri

*_Refs*\
Valore Integer che consente di specificare il tipo di gestione della memoria per l'oggetto.

*_Locname*\
Nome delle impostazioni locali.

### <a name="remarks"></a>Osservazioni

I valori possibili per il parametro *_Refs* e il loro significato sono:

- 0: la durata dell'oggetto è gestita dalle impostazioni locali che lo contengono.

- 1: la durata dell'oggetto deve essere gestita manualmente.

- \>1: Questi valori non sono definiti.

Il costruttore inizializza il relativo oggetto`_Refs`di base con **locale::**[facet](../standard-library/locale-class.md#facet_class)( ).

## <a name="collatecompare"></a><a name="compare"></a>fascicola::confronta

Confronta due sequenze di caratteri in base alle regole specifiche del relativo facet per verificarne l'uguaglianza o la disuguaglianza.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametri

*primo 1*\
Puntatore al primo elemento nella prima sequenza da confrontare.

*ultimo1*\
Puntatore all'ultimo elemento nella prima sequenza da confrontare.

*primo 2*\
Puntatore al primo elemento nella seconda sequenza da confrontare.

*ultimi2*\
Puntatore all'ultimo elemento nella seconda sequenza da confrontare.

### <a name="return-value"></a>Valore restituito

La funzione membro restituisce:

- - 1 se la prima sequenza ottiene un risultato inferiore nel confronto con la seconda sequenza.

- +1 se la seconda sequenza ottiene un risultato inferiore nel confronto con la prima sequenza.

- 0 se le sequenze sono equivalenti.

### <a name="remarks"></a>Osservazioni

La prima sequenza ottiene un risultato inferiore se contiene l'elemento più piccolo della prima coppia non equivalente rilevata nel confronto delle sequenze, oppure se non ci sono coppie non equivalenti, ma la prima sequenza è più breve.

La funzione membro `first1`restituisce `first2` `last2` [do_compare](#do_compare)( , `last1`, , ).

### <a name="example"></a>Esempio

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="collatedo_compare"></a><a name="do_compare"></a>fascicola::do_compare

Funzione virtuale chiamata per confrontare due sequenze di caratteri in base alle regole specifiche del relativo facet per verificarne l'uguaglianza o la disuguaglianza.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametri

*primo 1*\
Puntatore al primo elemento nella prima sequenza da confrontare.

*ultimo1*\
Puntatore all'ultimo elemento nella prima sequenza da confrontare.

*primo 2*\
Puntatore al primo elemento nella seconda sequenza da confrontare.

*ultimi2*\
Puntatore all'ultimo elemento nella seconda sequenza da confrontare.

### <a name="return-value"></a>Valore restituito

La funzione membro restituisce:

- - 1 se la prima sequenza ottiene un risultato inferiore nel confronto con la seconda sequenza.

- +1 se la seconda sequenza ottiene un risultato inferiore nel confronto con la prima sequenza.

- 0 se le sequenze sono equivalenti.

### <a name="remarks"></a>Osservazioni

La funzione membro virtuale protetta confronta la sequenza in corrispondenza di [ , first1, Last1 ) con la sequenza at *[ first2, last2*). Confronta i valori applicando `operator<` tra coppie di `CharType`elementi corrispondenti di tipo . La prima sequenza ottiene un risultato inferiore se contiene l'elemento più piccolo della prima coppia non equivalente rilevata nel confronto delle sequenze, oppure se non ci sono coppie non equivalenti, ma la prima sequenza è più breve.

### <a name="example"></a>Esempio

Vedere l'esempio di [collate::compare](#compare), che chiama `do_compare`.

## <a name="collatedo_hash"></a><a name="do_hash"></a>fascicola::do_hash

Funzione virtuale chiamata per determinare il valore hash delle sequenze in base alle regole specifiche del relativo facet.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Prima*\
Un puntatore al primo carattere nella sequenza il cui valore deve essere determinato.

*Ultima*\
Un puntatore all'ultimo carattere nella sequenza il cui valore deve essere determinato.

### <a name="return-value"></a>Valore restituito

Valore hash di tipo **long** per la sequenza.

### <a name="remarks"></a>Osservazioni

Un valore hash può essere utile, ad esempio, per distribuire le sequenze in modo pseudo-casuale all'interno di una matrice di elenchi.

### <a name="example"></a>Esempio

Vedere l'esempio di [hash](#hash), che chiama `do_hash`.

## <a name="collatedo_transform"></a><a name="do_transform"></a>fascicola::do_trasformazione

Funzione virtuale chiamata per convertire una sequenza di caratteri in una stringa che può essere utilizzata nei confronti lessicografici con altre sequenze di caratteri convertite in modo analogo dalle stesse impostazioni locali.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Prima*\
Puntatore al primo carattere nella sequenza da convertire.

*Ultima*\
Puntatore all'ultimo carattere nella sequenza da convertire.

### <a name="return-value"></a>Valore restituito

Stringa corrispondente alla sequenza di caratteri trasformata.

### <a name="remarks"></a>Osservazioni

La funzione membro virtuale protetta restituisce un oggetto della classe `first` `last` [string_type](#string_type) la cui sequenza controllata è una copia della sequenza [ , ). Se una classe derivata da collate\< **CharType**> esegue l'override di [do_compare](#do_compare), per corrispondere deve anche eseguire l'override di `do_transform`. Quando vengono passate a `collate::compare`, due stringhe trasformate devono produrre lo stesso risultato che si otterrebbe dal passaggio delle stringhe non trasformate per il confronto nella classe derivata.

### <a name="example"></a>Esempio

Vedere l'esempio di [transform](#transform) che chiama `do_transform`.

## <a name="collatehash"></a><a name="hash"></a>fascicola::hash

Determina il valore hash della sequenza in base alle regole specifiche del relativo facet.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Prima*\
Un puntatore al primo carattere nella sequenza il cui valore deve essere determinato.

*Ultima*\
Un puntatore all'ultimo carattere nella sequenza il cui valore deve essere determinato.

### <a name="return-value"></a>Valore restituito

Valore hash di tipo **long** per la sequenza.

### <a name="remarks"></a>Osservazioni

La funzione [do_hash](#do_hash)membro `first`restituisce do_hash ( , `last`).

Un valore hash può essere utile, ad esempio, per distribuire le sequenze in modo pseudo-casuale all'interno di una matrice di elenchi.

### <a name="example"></a>Esempio

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="collatestring_type"></a><a name="string_type"></a>fascicola::string_type

Tipo che descrive una stringa di tipo `basic_string` contenente caratteri di tipo `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Osservazioni

Il tipo descrive una specializzazione del modello di classe [basic_string](../standard-library/basic-string-class.md) i cui oggetti possono archiviare copie della sequenza di origine.

### <a name="example"></a>Esempio

Per un esempio di dichiarazione e uso di `string_type`, vedere [transform](#transform).

## <a name="collatetransform"></a><a name="transform"></a>fascicola::trasformazione

Converte una sequenza di caratteri dalle impostazioni locali in una stringa che può essere utilizzata nei confronti lessicografici con altre sequenze di caratteri convertite in modo analogo dalle stesse impostazioni locali.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametri

*Prima*\
Puntatore al primo carattere nella sequenza da convertire.

*Ultima*\
Puntatore all'ultimo carattere nella sequenza da convertire.

### <a name="return-value"></a>Valore restituito

Stringa contenente la sequenza di caratteri trasformata.

### <a name="remarks"></a>Osservazioni

La funzione [do_transform](#do_transform)membro`first`restituisce do_transform ( , `last`).

### <a name="example"></a>Esempio

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>Vedere anche

[\<>delle impostazioni locali](../standard-library/locale.md)\
[Sicurezza dei filettatura nella libreria standard di C](../standard-library/thread-safety-in-the-cpp-standard-library.md)
