---
title: "Intervalli dei tipi di dati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "unsigned"
  - "wchar_t"
  - "char"
  - "signed"
  - "short"
  - "long"
  - "double"
  - "float"
  - "int"
  - "long_double"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "float (parola chiave) [C++]"
  - "char (parola chiave) [C++]"
  - "unsigned long"
  - "__wchar_t (parola chiave) [C++]"
  - "unsigned short int"
  - "enum (parola chiave)"
  - "unsigned char (parola chiave) [C++]"
  - "tipo di dati Integer, intervalli dei tipi di dati"
  - "tipo di dati int"
  - "tipi di dati [C++], intervalli"
  - "unsigned int"
  - "tipo di dati short"
  - "dati short int"
  - "tipi con segno [C++], intervalli dei tipi di dati"
  - "long long (parola chiave) [C++]"
  - "long double (parola chiave) [C++]"
  - "tipo di dati Double, intervalli dei tipi di dati"
  - "signed short int"
  - "unsigned short"
  - "tipi Integer con dimensione"
  - "signed int"
  - "signed long int"
  - "signed char (parola chiave) [C++]"
  - "wchar_t (parola chiave) [C++]"
  - "long (parola chiave) [C++]"
  - "intervalli [C++]"
  - "tipi senza segno [C++], intervalli dei tipi di dati"
  - "numeri a virgola mobile, intervalli dei tipi di dati"
  - "intervalli [C++], tipi di dati"
  - "long int (parola chiave) [C++]"
  - "unsigned long int"
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# Intervalli dei tipi di dati
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

I compilatori di Visual C++ a 32 e a 64 bit riconoscono i tipi indicati nella tabella più avanti in questo articolo.  
  
-   `int` (`unsigned``int`)  
  
-   `__int8` (`unsigned``__int8`)  
  
-   `__int16` (`unsigned``__int16`)  
  
-   `__int32` (`unsigned``__int32`)  
  
-   `__int64` (`unsigned``__int64`)  
  
-   `short` (`unsigned``short`)  
  
-   `long` (`unsigned``long`)  
  
-   `long` `long` (`unsigned``long``long`)  
  
 Se il nome inizia con due caratteri di sottolineatura (`__`), un tipo di dati non è standard.  
  
 Gli intervalli specificati nella tabella seguente sono inclusivo-inclusivo.  
  
|Nome tipo|Byte|Altri nomi|Intervallo di valori|  
|---------------|-----------|-----------------|---------------------|  
|int|4|signed|Da –2,147,483,648 a 2,147,483,647|  
|unsigned int|4|unsigned|Da 0 a 4.294.967.295|  
|__int8|1|char|da –128 a 127|  
|unsigned __int8|1|unsigned char|Da 0 a 255|  
|__int16|2|short, short int, signed short int|Da –32,768 a 32,767|  
|unsigned __int16|2|unsigned short, unsigned short int|Da 0 a 65.535|  
|__int32|4|signed, signed int, int|Da –2,147,483,648 a 2,147,483,647|  
|unsigned __int32|4|unsigned, unsigned int|Da 0 a 4.294.967.295|  
|__int64|8|long long, signed long long|Da –9,223,372,036,854,775,808 a 9,223,372,036,854,775,807|  
|unsigned __int64|8|unsigned long long|Da 0 a 18.446.744.073.709.551.615|  
|bool|1|nessuno|false o true|  
|char|1|nessuno|Da –128 a 127 per impostazione predefinita<br /><br /> Da 0 a 255 quando viene compilato usando [/J](../build/reference/j-default-char-type-is-unsigned.md)|  
|signed char|1|nessuno|da –128 a 127|  
|unsigned char|1|nessuno|Da 0 a 255|  
|short|2|short int, signed short int|Da –32,768 a 32,767|  
|unsigned short|2|unsigned short int|Da 0 a 65.535|  
|long|4|long int, signed long int|Da –2,147,483,648 a 2,147,483,647|  
|unsigned long|4|unsigned long int|Da 0 a 4.294.967.295|  
|long long|8|none (ma equivalente a __int64)|Da –9,223,372,036,854,775,808 a 9,223,372,036,854,775,807|  
|unsigned long long|8|none (ma equivalente a __int64 non firmato)|Da 0 a 18.446.744.073.709.551.615|  
|enum|varies|none|Vedere le [note](#bkmkRemarks) più avanti in questo articolo|  
|mobile|4|nessuno|3.4E +/- 38 (7 cifre)|  
|double|8|nessuno|1.7E +/- 308 (15 cifre)|  
|long double|uguale a double|nessuno|Uguale a double|  
|wchar_t|2|__wchar_t|Da 0 a 65.535|  
  
 In base a come viene usata, una variabile di `__wchar_t` indica un tipo di carattere wide o un tipo di carattere multibyte. Usare il prefisso `L` prima di una costante di carattere o di stringa per definire la costante del tipo di carattere wide.  
  
 `signed` e `unsigned` sono modificatori che è possibile usare con qualsiasi tipo integrale eccetto `bool`. Si noti che `char`, `signed char` e `unsigned char` sono tre tipi diversi per scopi di meccanismi come l'overload e i modelli.  
  
 I tipi `int` e `unsigned``int` hanno una dimensione di quattro byte. Tuttavia, il codice portatile non deve dipendere dalla dimensione di `int` poiché lo standard del linguaggio gli consente di essere specifico dell'implementazione.  
  
 C/C++ in Visual Studio supporta inoltre tipi di Integer dimensionati. Per altre informazioni, vedere [__int8, \__int16, \__int32, \__int64](../cpp/int8-int16-int32-int64.md) e [Limiti per tipi Integer](../cpp/integer-limits.md).  
  
 Per altre informazioni sulle restrizioni della dimensione di ogni tipo, vedere [Tipi fondamentali](../cpp/fundamental-types-cpp.md).  
  
 L'intervallo dei tipi enumerati varia a seconda del contesto del linguaggio e dei flag del compilatore specificati. Per altre informazioni, vedere [Dichiarazioni di enumerazioni C](../c-language/c-enumeration-declarations.md) e [Enumerazioni](../cpp/enumerations-cpp.md).  
  
## Vedere anche  
 [Parole chiave](../cpp/keywords-cpp.md)   
 [Tipi fondamentali](../cpp/fundamental-types-cpp.md)