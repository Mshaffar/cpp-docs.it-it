---
title: "Stringa e valori letterali carattere (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "R"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sequenze di escape"
  - "L (costante)"
  - "valori letterali stringa"
  - "valori letterali stringa, C++"
  - "stringhe Null"
  - "stringhe Null, stringhe con terminazione Null"
  - "NULL, costante carattere"
  - "valori letterali stringa"
  - "valori letterali stringa, sintassi"
  - "stringhe [C++], valori letterali stringa"
  - "caratteri wide, stringhe"
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Stringa e valori letterali carattere (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ supporta diversi tipi di stringa e di carattere e permette di esprimere i valori letterali di ogni tipo. Nel codice sorgente, si esprime il contenuto dei valori letterali carattere e stringa usando un set di caratteri. I nomi di caratteri universali e i caratteri di escape consentono di esprimere qualsiasi stringa usando solo il set di caratteri di origine di base. Un valore letterale stringa non elaborata permette di evitare l'uso di caratteri di escape e può essere usato per esprimere tutti i tipi di valori letterali stringa. È anche possibile creare valori letterali std::string senza dover eseguire ulteriori passaggi di costruzione o conversione.  
  
```cpp  
#include <string> using namespace std::string_literals; // enables s-suffix for std::string literals int main() { // Character literals auto c0 =   'A'; // char auto c1 = u8'A'; // char auto c2 =  L'A'; // wchar_t auto c3 =  u'A'; // char16_t auto c4 =  U'A'; // char32_t // String literals auto s0 =   "hello"; // const char* auto s1 = u8"hello"; // const char*, encoded as UTF-8 auto s2 =  L"hello"; // const wchar_t* auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16 auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32 // Raw string literals containing unescaped \ and " auto R0 =   R"("Hello \ world")"; // const char* auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8 auto R2 =  LR"("Hello \ world")"; // const wchar_t* auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16 auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32 // Combining string literals with standard s-suffix auto S0 =   "hello"s; // std::string auto S1 = u8"hello"s; // std::string auto S2 =  L"hello"s; // std::wstring auto S3 =  u"hello"s; // std::u16string auto S4 =  U"hello"s; // std::u32string // Combining raw string literals with standard s-suffix auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char* auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8 auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t* auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16 auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32 }  
```  
  
 I valori letterali stringa non hanno prefisso o prefissi `u8`, `L`, `u` e `U` per indicare rispettivamente le codifiche di caratteri narrow \(a byte singolo o multibyte\), UTF\-8, caratteri wide \(UCS\-2 o UTF\-16\), UTF\-16 e UTF\-32. Un valore letterale stringa non elaborata può avere i prefissi `R`, `u8R`, `LR`, `uR` e `UR` per gli equivalenti della versione non elaborata di queste codifiche.  Per creare valori std::string temporanei o statici, è possibile usare valori letterali stringa o valori letterali stringa non elaborata con un suffisso `s`. Per altre informazioni, vedere la sezione Valori letterali stringa riportata di seguito. Per altre informazioni sul set di caratteri di origine di base, sui nomi di caratteri universali e sull'uso di caratteri dalle tabelle codici estese nel codice sorgente, vedere [Set di caratteri](../cpp/character-sets2.md).  
  
## Valori letterali carattere  
 Un *valore letterale carattere* è costituito da un carattere costante. È rappresentato dal carattere racchiuso tra virgolette singole. Sono disponibili quattro tipi di valori letterali carattere:  
  
-   Valori letterali carattere "narrow" di tipo `char`, ad esempio `'a'`  
  
-   Valori letterali carattere wide di tipo `wchar_t`, ad esempio `L'a'`  
  
-   Valori letterali carattere wide di tipo `char16_t`, ad esempio `u'a'`  
  
-   Valori letterali carattere wide di tipo `char32_t`, ad esempio `U'a'`  
  
 Il carattere usato per un valore letterale carattere può essere un carattere qualsiasi, a eccezione dei caratteri riservati, quali il carattere di barra rovesciata \('\\'\), virgoletta singola \('\) o nuova riga. I caratteri riservati possono essere specificati con una sequenza di escape. È possibile specificare i caratteri usando nomi di caratteri universali, a condizione che le dimensioni del tipo siano sufficienti a contenere il carattere.  
  
###  <a name="bkmk_Escape"></a> Sequenze di escape  
 Esistono tre tipi di sequenze di escape: semplici, ottali ed esadecimali. Le sequenze di escape possono essere una delle seguenti:  
  
|Valore|Sequenza di escape|Valore|Sequenza di escape|  
|------------|------------------------|------------|------------------------|  
|carattere di nuova riga|\\n|barra rovesciata|\\\\|  
|tabulazione orizzontale|\\t|punto interrogativo|? o \\?|  
|tabulazione verticale|\\v|virgoletta singola|\\'|  
|BACKSPACE|\\b|virgoletta doppia|\\"|  
|ritorno a capo|\\r|carattere null|\\0|  
|avanzamento carta|\\f|ottale|\\ooo|  
|avviso \(campana\)|\\a|esadecimale|\\xhhh|  
  
 Il codice seguente illustra alcuni esempi di caratteri di escape con valori letterali stringa a caratteri "narrow". La stessa sintassi è valida per altri tipi di valori letterali stringa.  
  
```cpp  
#include <iostream> using namespace std; int main() { char newline = '\n'; char tab = '\t'; char backspace = '\b'; char backslash = '\\'; char nullChar = '\0'; cout << "Newline character: " << newline << "ending" << endl; // Newline character: //  ending cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending }  
```  
  
 **Sezione specifica Microsoft**  
  
 Per creare un valore da un valore letterale carattere privo di prefisso, il compilatore converte il carattere o la sequenza di caratteri tra virgolette singole in valori a 8 bit entro un valore intero a 32 bit. Più caratteri nel valore letterale carattere riempiono i byte corrispondenti secondo le necessità, dal più significativo al meno significativo. Per creare un valore `char`, il compilatore prende il byte meno significativo. Per creare un valore `wchar_t` o  `char16_t`, il compilatore prende la parola meno significativa. Il compilatore avvisa che il risultato sarà troncato se si assegnano bit al di sopra del byte o della parola assegnati.  
  
```cpp  
char c0    = 'abcd';    // C4305, C4309, truncates to 'd' wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'  
```  
  
 Una sequenza di escape ottale è una barra rovesciata seguita da una sequenza di un massimo di 3 cifre ottali. Il comportamento di una sequenza di escape ottale che sembra contenere più di tre cifre viene trattato come una sequenza di escape ottale seguita dalle cifre successive come caratteri: il risultato può essere sorprendente. Ad esempio:  
  
```cpp  
char c1 = '\100';   // '@' char c2 = '\1000';  // C4305, C4309, truncates to '0'   
```  
  
 Le sequenze di escape che sembrano contenere caratteri non ottali vengono valutate come una sequenza ottale fino all'ultimo carattere non ottale, seguita dai caratteri rimanenti. Ad esempio:  
  
```cpp  
char c3 = '\009';   // '9' char c4 = '\089';   // C4305, C4309, truncates to '9' char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'  
```  
  
 Una sequenza di escape esadecimale è una barra rovesciata seguita dal carattere `x`, seguito a sua volta da una sequenza di cifre esadecimali. Una sequenza di escape che non contiene cifre esadecimali causa l'errore C2153 del compilatore: "i valori letterali esadecimali devono avere almeno una cifra esadecimale". Gli zero iniziali vengono ignorati. Una sequenza di escape che sembra contenere caratteri esadecimali e non esadecimali viene valutata come sequenza di escape esadecimale fino all'ultimo carattere non esadecimale, seguita dai caratteri esadecimali.   In un valore letterale carattere "narrow" senza prefisso o con prefisso u8 il valore esadecimale più elevato è 0xff. In un valore letterale carattere wide con prefisso L o u il valore esadecimale più elevato è 0xFFFF. In un valore letterale carattere wide con prefisso U il valore esadecimale più elevato è 0xFFFFFFFF.  
  
```cpp  
char c6 = '\x0050'; // 'P' char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'  
```  
  
 Se un valore letterale carattere wide preceduto da `L` contiene più di un carattere, il valore viene ricavato dal primo carattere. I caratteri successivi vengono ignorati, a differenza del comportamento dell'equivalente valore letterale carattere "narrow" senza prefisso.  
  
```cpp  
wchar_t w1 = L'\100';   // L'@' wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored wchar_t w6 = L'\x0050'; // L'P' wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored  
```  
  
 **Fine sezione specifica Microsoft**  
  
 Il carattere \(\\\) è un carattere di continuazione di riga, quando viene posizionato alla fine di una riga. Se si vuole che un carattere barra rovesciata venga visualizzato come un valore letterale carattere, è necessario digitare due barre rovesciate di seguito in una riga \(`\\`\). Per altre informazioni sul carattere di continuazione di riga, vedere [Fasi di conversione](../preprocessor/phases-of-translation.md).  
  
###  <a name="bkmk_UCN"></a> Nomi di caratteri universali  
 Nei valori letterali carattere e nei valori letterali stringa \(elaborati\) nativi, qualsiasi carattere potrà essere rappresentato da un nome di carattere universale.  I nomi di caratteri universali sono formati da un prefisso \\U seguito da un punto di codice Unicode a otto cifre oppure da un prefisso \\u seguito da un punto di codice Unicode a quattro cifre. Tutte e otto o quattro cifre devono rispettivamente essere presenti per costituire un nome di carattere universale in formato corretto.  
  
```cpp  
char u1 = 'A';          // 'A' char u2 = '\101';       // octal, 'A' char u3 = '\x41';       // hexadecimal, 'A' char u4 = '\u0041';     // \u UCN 'A' char u5 = '\U00000041'; // \U UCN 'A'  
```  
  
 **Coppie di surrogati**  
  
 I nomi di caratteri universali non possono codificare i valori nell'intervallo di punti di codice surrogati D800\-DFFF. Per le coppie di surrogati Unicode, specificare il nome di carattere universale usando `\UNNNNNNNN`, dove NNNNNNNN è il punto di codice a otto cifre per il carattere. Il compilatore genera una coppia di surrogati se richiesto.  
  
 In C\+\+03 il linguaggio consentiva solo la rappresentazione di un subset di caratteri con i rispettivi nomi di caratteri universali e consentiva alcuni nomi di caratteri universali che non rappresentano effettivamente caratteri Unicode validi. Questo problema è stato risolto nello standard C\+\+11. In C\+\+11, sia i valori letterali carattere sia i valori letterali stringa possono usare i nomi di caratteri universali.  Per altre informazioni sui nomi di caratteri universali, vedere [Set di caratteri](../cpp/character-sets2.md). Per altre informazioni su Unicode, vedere [Unicode](http://msdn.microsoft.com/library/dd374081\(v=vs.85\).aspx). Per altre informazioni sulle coppie di surrogati, vedere la pagina relativa alle [coppie di surrogati e ai caratteri supplementari](http://msdn.microsoft.com/library/dd374069\(v=vs.85\).aspx).  
  
## Valori letterali stringa  
 Un valore letterale stringa rappresenta una sequenza di caratteri che insieme formano una stringa con terminazione null. I caratteri devono essere racchiusi tra virgolette doppie. Sono disponibili i seguenti tipi di valori letterali stringa:  
  
### Valori letterali stringa a caratteri "narrow"  
 Un valore letterale stringa a caratteri "narrow" è una matrice senza prefisso, delimitata da virgolette doppie e con terminazione Null di tipo `const` `char`\[`n`\], in cui n è la lunghezza della matrice in byte. Un valore letterale stringa a caratteri "narrow" può contenere qualsiasi carattere grafico eccetto le virgolette doppie \(`"`\), la barra rovesciata \(`\`\) o un carattere di nuova riga. Un valore letterale stringa a caratteri "narrow" può anche contenere le sequenze di escape sopra elencate e i nomi di caratteri universali che rientrano in un byte.  
  
```cpp  
const char *narrow = "abcd"; // represents the string: yes\no const char *escaped = "yes\\no";  
```  
  
 **Stringhe codificate UTF\-8**  
  
 Una stringa codificata UTF\-8 è una matrice con prefisso u8, delimitata da virgolette doppie e con terminazione Null di tipo `const` `char`\[`n`\], in cui n è la lunghezza della matrice codificata in byte. Un valore letterale stringa con prefisso u8 può contenere qualsiasi carattere grafico eccetto le virgolette doppie \(`"`\), la barra rovesciata \(`\`\) o un carattere di nuova riga. Un valore letterale stringa con prefisso u8 può anche contenere le sequenze di escape sopra elencate e qualsiasi nome di carattere universale.  
  
```cpp  
const char* str1 = u8"Hello World"; const char* str2 = u8"\U0001F607 is O:-)";  
```  
  
### Valori letterali stringa a caratteri wide  
 Un valore letterale stringa a caratteri wide è una matrice con terminazione Null della costante `wchar_t` con prefisso '`L`' contenente qualsiasi carattere grafico eccetto le virgolette doppie \("\), la barra rovesciata \(\\\) o un carattere di nuova riga. Un valore letterale stringa a caratteri wide può contenere le sequenze di escape sopra elencate e qualsiasi nome di carattere universale.  
  
```cpp  
const wchar_t* wide = L"zyxw"; const wchar_t* newline = L"hello\ngoodbye";  
```  
  
 **char16\_t e char32\_t \(C\+\+11\)**  
  
 C\+\+11 introduce i tipi di carattere portabili `char16_t` \(Unicode a 16 bit\) e `char32_t` \(Unicode a 32 bit\):  
  
```cpp  
auto s3 = u"hello"; // const char16_t* auto s4 = U"hello"; // const char32_t*  
```  
  
### Valori letterali stringa non elaborata \(C\+\+11\)  
 Un valore letterale stringa non elaborata è una matrice con terminazione Null di qualsiasi tipo di carattere contenente qualsiasi carattere grafico, inclusi le virgolette doppie \("\), la barra rovesciata \(\\\) o un carattere di nuova riga. I valori letterali stringa non elaborata vengono spesso usati nelle espressioni regolari che usano le classi di caratteri e nelle stringhe HTML e XML. Per gli esempi vedere la pagina relativa alle [domande frequenti di Bjarne Stroustrup su C\+\+11](http://go.microsoft.com/fwlink/?LinkId=401172).  
  
```cpp  
// represents the string: An unescaped \ character const char* raw_narrow = R"(An unescaped \ character)"; const wchar_t* raw_wide = LR"(An unescaped \ character)"; const char*       raw_utf8  = u8R"(An unescaped \ character)"; const char16_t* raw_utf16 = uR"(An unescaped \ character)"; const char32_t* raw_utf32 = UR"(An unescaped \ character)";  
```  
  
 Un delimitatore è una sequenza definita dall'utente, contenente un massimo di 16 caratteri, che precede immediatamente la parentesi di apertura e segue immediatamente la parentesi di chiusura di un valore letterale stringa non elaborata.  Ad esempio, in `R"abc(Hello"\()abc"` la sequenza delimitatore è `abc` e il contenuto stringa è `Hello"\(`. È possibile usare un delimitatore per evitare ambiguità tra stringhe non elaborate contenenti sia virgolette doppie che parentesi. Ciò provoca un errore del compilatore:  
  
```cpp  
// meant to represent the string: )” const char* bad_parens = R"()")";  // error C2059  
```  
  
 Tuttavia, un delimitatore è in grado di risolvere tale errore:  
  
```cpp  
const char* good_parens = R"xyz()")xyz";  
```  
  
 È possibile costruire un valore letterale stringa non elaborata in cui è presente una nuova riga \(non un carattere di escape\) nell'origine:  
  
```cpp  
// represents the string: hello //goodbye const wchar_t* newline = LR"(hello goodbye)";  
```  
  
### Valori letterali std::string \(C\+\+14\)  
 I valori letterali std::string sono implementazioni della libreria standard di valori letterali definiti dall'utente \(vedere più avanti\), rappresentati come "xyx"s \(con un suffisso `s`\). Questo tipo di valore letterale stringa produce un oggetto temporaneo di tipo std::string, std::wstring, std::u32string o std::u16string, in base al prefisso specificato. Se non viene usato alcun prefisso, come sopra, verrà prodotto un valore letterale std::string. L"xyz"s produce un valore letterale std::wstring. u"xyz"s produce un valore letterale [std::u16string](../Topic/u16string.md) e U"xyz"s produce un valore letterale [std::u32string](../Topic/u32string.md).  
  
```cpp  
//#include <string> //using namespace std::string_literals; string str{ "hello"s }; string str2{ u8"Hello World" }; wstring str3{ L"hello"s }; u16string str4{ u"hello"s }; u32string str5{ U"hello"s };  
```  
  
 Il suffisso s può essere usato anche su valori letterali stringa non elaborati:  
  
```cpp  
u32string str6{ UR"(She said "hello.")"s };  
```  
  
 I valori letterali stringa std::string vengono definiti nello spazio dei nomi `std::literals::string_literals` nel file di intestazione \<string\>. Poiché `std::literals::string_literals` e `std::literals` sono dichiarati come [spazi dei nomi inline](../cpp/namespaces-cpp.md), `std::literals::string_literals` verrà considerato automaticamente come appartenente direttamente allo spazio dei nomi `std`.  
  
### Dimensioni dei valori letterali stringa  
 Per una stringa char\* ANSI e altre codifiche a byte singolo \(non UTF\-8\), le dimensioni \(in byte\) di un valore letterale stringa corrispondono al numero di caratteri più 1 \(per il carattere Null di terminazione\). Per tutti gli altri tipi di stringa, le dimensioni non sono strettamente correlate al numero di caratteri. UTF\-8 usa al massimo quattro elementi di tipo char per codificare alcune *unità di codice* e char16\_t o wchar\_t codificati come UTF\-16 possono usare due elementi \(per un totale di quattro byte\) per codificare una singola *unità di codice*.   Questo esempio illustra la dimensione di un valore letterale stringa a caratteri wide in byte:  
  
```cpp  
const wchar_t* str = L"Hello!"; const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);  
```  
  
 Si noti che `strlen()` e `wcslen()` non includono le dimensioni del carattere Null di terminazione, le cui dimensioni sono uguali alle dimensioni di elemento del tipo di stringa: un byte in una stringa char\*, due byte in stringhe wchar\_t\* o char16\_t\* e quattro byte in stringhe char32\_t\*.  
  
 La lunghezza massima di un valore letterale stringa è di 65.535 byte. Questo limite si applica sia ai valori letterali stringa a caratteri narrow che a quelli a caratteri wide.  
  
### Modifica dei valori letterali stringa  
 Poiché i valori letterali stringa, esclusi std:string, sono delle costanti, il tentativo di modificarli, ad esempio str\[2\] \= 'A', causa un errore del compilatore.  
  
 **Sezione specifica Microsoft**  
  
 In Visual C\+\+ è possibile usare un valore letterale stringa per inizializzare un puntatore a `char` o `wchar_t` non const. Questa operazione è consentita nel codice C99, ma è deprecata in C\+\+98 e rimossa in C\+\+11. Il tentativo di modificare la stringa genera una violazione di accesso, come nel seguente esempio:  
  
```cpp  
wchar_t* str = L"hello"; str[2] = L'a'; // run-time error: access violation  
```  
  
 È possibile fare in modo che il compilatore generi un errore quando un valore letterale stringa viene convertito in un puntatore di caratteri non\_const quando si imposta l'opzione del compilatore [\/Zc:strictStrings \(Disabilitare la conversione del tipo di valore letterale stringa\)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md). È consigliabile usarlo per il codice portabile conforme agli standard. È anche consigliabile usare la parola chiave `auto` per dichiarare i puntatori inizializzati dal valore letterale stringa perché viene risolta nel tipo \(const\) corretto. Ad esempio, l'esempio di codice seguente rileva un tentativo di scrittura in un valore letterale stringa in fase di compilazione:  
  
```cpp  
auto str = L"hello"; str[2] = L'a'; // C3892: you cannot assign to a variable that is const.  
```  
  
 In alcuni casi, i valori letterali stringa identici possono essere inseriti in un pool per risparmiare spazio nel file eseguibile. Nel pool di valori letterali stringa il compilatore genera tutti i riferimenti a un valore letterale stringa particolare in modo che punti alla stessa posizione di memoria, anziché avere ogni riferimento che punta a un'istanza separata del valore letterale stringa. Per abilitare la condivisione delle stringhe, usare l'opzione del compilatore [\/GF](../build/reference/gf-eliminate-duplicate-strings.md).  
  
 **Fine sezione specifica Microsoft**  
  
### Concatenazione dei valori letterali stringa adiacenti  
 I valori letterali stringa adiacenti a caratteri wide o narrow sono concatenati. La seguente dichiarazione:  
  
```cpp  
char str[] = "12" "34";  
```  
  
 è identica a questa dichiarazione:  
  
```cpp  
char atr[] = "1234";  
```  
  
 e a questa dichiarazione:  
  
```cpp  
char atr[] =  "12\ 34";  
```  
  
 L'uso di codici di escape esadecimali incorporati per specificare i valori letterali stringa può provocare risultati imprevisti. L'esempio seguente prova a creare un valore letterale stringa contenente il carattere ASCII 5, seguito dai caratteri f, i, v ed e:  
  
```cpp  
"\x05five"  
```  
  
 Il risultato effettivo è un 5F esadecimale, ovvero il codice ASCII per un carattere di sottolineatura, seguito dai caratteri i, v ed e. Per ottenere il risultato corretto, è possibile usare uno dei seguenti codici:  
  
```cpp  
"\005five"     // Use octal literal. "\x05" "five"  // Use string splicing.  
```  
  
 I valori letterali std::string, in quanto tipi std::string, possono essere concatenati con l'operatore \+ definito per i tipi [basic\_string](../standard-library/basic-string-class.md). Possono essere concatenati anche in modo analogo ai valori letterali stringa adiacenti. In entrambi i casi, la codifica della stringa e il suffisso devono corrispondere:  
  
```cpp  
auto x1 = "hello" " " " world"; // OK auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes  
```  
  
### Valori letterali stringa con nomi di caratteri universali  
 I valori letterali stringa \(elaborata\) nativi possono usare i nomi di caratteri universali per rappresentare qualsiasi carattere a condizione che il nome di carattere universale possa essere codificato come uno o più caratteri nel tipo di stringa.  Ad esempio, un nome di carattere universale che rappresenta un carattere esteso non può essere codificato in una stringa a caratteri narrow usando la tabella codici ANSI, ma può essere codificato in stringhe a caratteri narrow in alcune tabelle di codici multibyte o in stringhe UTF\-8 o in una stringa a caratteri wide. In C\+\+11 il supporto Unicode viene esteso dai tipi di stringa char16\_t\* e char32\_t\*:  
  
```cpp  
// ASCII smiling face const char*     s1 = ":-)"; // UTF-16 (on Windows) encoded WINKING FACE (U+1F609) const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)"; // UTF-8  encoded SMILING FACE WITH HALO (U+1F607) const char*     s3 = u8"😇 = \U0001F607 is O:-)"; // UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603) const char16_t* s4 = u"😃 = \U0001F603 is :-D"; // UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E) const char32_t* s5 = U"😎 = \U0001F60E is B-)";  
```  
  
## Vedere anche  
 [Set di caratteri](../cpp/character-sets2.md)   
 [Valori letterali numerici, booleani e puntatore](../cpp/numeric-boolean-and-pointer-literals-cpp.md)   
 [Valori letterali definiti dall'utente](../cpp/user-defined-literals-cpp.md)