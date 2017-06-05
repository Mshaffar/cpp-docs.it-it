---
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
dev_langs:
- C++
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 4a66ac6c57b2e4ae25c7496152b4e113f3bbf751
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="strncmp-wcsncmp-mbsncmp-mbsncmpl"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
Esegue il confronto del numero specificato di caratteri delle due stringhe.  
  
> [!IMPORTANT]
>  `_mbsncmp` e `_mbsncmp_l` non possono essere usati nelle applicazioni eseguite in Windows Runtime. Per altre informazioni, vedere l'articolo relativo alle [funzioni CRT non supportate con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintassi  
  
```  
int strncmp(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int wcsncmp(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsncmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,   
   _locale_t locale  
);int _mbsnbcmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `string1, string2`  
 Stringhe da confrontare.  
  
 `count`  
 Numero di caratteri da confrontare.  
  
 `locale`  
 Impostazioni locali da usare.  
  
## <a name="return-value"></a>Valore restituito  
 Il valore restituito indica la relazione delle sottostringhe di `string1` e `string2` come descritto di seguito.  
  
|Valore restituito|Descrizione|  
|------------------|-----------------|  
|< 0|La sottostringa di `string1` è minore della sottostringa di `string2`|  
|0|La sottostringa di `string1` è identica alla sottostringa di `string2`|  
|> 0|La sottostringa di `string1` è maggiore della sottostringa di `string2`|  
  
 In caso di errore di convalida dei parametri, `_mbsncmp` e `_mbsncmp_l` restituiscono `_NLSCMPERROR`, definito in \<string.h> e \<mbstring.h>.  
  
## <a name="remarks"></a>Note  
 La funzione `strncmp` esegue un confronto ordinale al massimo dei primi `count` caratteri in `string1` e `string2`, quindi restituisce un valore che indica la relazione tra le sottostringhe. `strncmp` è una versione di `_strnicmp` che effettua la distinzione tra maiuscole e minuscole. `wcsncmp` e `_mbsncmp` sono versioni con distinzione tra maiuscole e minuscole di `_wcsnicmp` e `_mbsnicmp`.  
  
 `wcsncmp` e `_mbsncmp` sono versioni con caratteri wide e caratteri multibyte di `strncmp`. Gli argomenti di `wcsncmp` sono stringhe di caratteri wide, mentre gli argomenti di `_mbsncmp` sono stringhe di caratteri multibyte. `_mbsncmp` riconosce le sequenze di caratteri multibyte in base alla tabella codici multibyte corrente e restituisce `_NLSCMPERROR` in caso di errore.  
  
 Inoltre, `_mbsncmp` e `_mbsncmp_l` convalidano i parametri. Se `string1` o `string2` è un puntatore Null, viene richiamato il gestore di parametri non validi, come descritto in [Convalida dei parametri](../../c-runtime-library/parameter-validation.md). Se l'esecuzione può continuare, `_mbsncmp` e `_mbsncmp_l` restituiscono `_NLSCMPERROR` e impostano `errno` su `EINVAL`. `strncmp` e `wcsncmp` non convalidano i parametri. A parte ciò, queste funzioni si comportano in modo identico.  
  
 Il comportamento di confronto di `_mbsncmp` e `_mbsncmp_l` è interessato dall'impostazione della categoria `LC_CTYPE` delle impostazioni locali. Controlla il rilevamento dei byte iniziali e finali dei caratteri multibyte. Per altre informazioni, vedere [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). La funzione `_mbsncmp` usa le impostazioni locali correnti per questo comportamento dipendente dalle impostazioni locali. La funzione `_mbsncmp_l` è identica ad eccezione del fatto che usa il parametro `locale`. Per altre informazioni, vedere [Impostazioni locali](../../c-runtime-library/locale.md). Se le impostazioni locali sono a un byte, il comportamento di queste funzioni è identico a `strncmp`.  
  
### <a name="generic-text-routine-mappings"></a>Mapping di routine di testo generico  
  
|Routine TCHAR.H|_UNICODE e _MBCS non definiti|_MBCS definito|_UNICODE definito|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsnccmp`|`strncmp`|`_mbsncmp`|`wcsncmp`|  
|`_tcsncmp`|`strncmp`|`_mbsnbcmp`|`wcsncmp`|  
|`_tccmp`|Mapping a una macro o a una funzione inline|`_mbsncmp`|Mapping a una macro o a una funzione inline|  
|**non applicabile**|**non applicabile**|`_mbsncmp_l`|**non applicabile**|  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`strncmp`|\<string.h>|  
|`wcsncmp`|\<string.h> o \<wchar.h>|  
|`_mbsncmp`, `_mbsncmp_l`|\<mbstring.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Esempio  
  
```  
// crt_strncmp.c  
#include <string.h>  
#include <stdio.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown fox jumps over the lazy dog";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
   printf( "Compare strings:\n      %s\n      %s\n\n",  
           string1, string2 );  
   printf( "Function:   strncmp (first 10 characters only)\n" );  
   result = strncmp( string1, string2 , 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n\n", tmp );  
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );  
   result = _strnicmp( string1, string2, 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n", tmp );  
}  
```  
  
```Output  
Compare strings:  
      The quick brown dog jumps over the lazy fox  
      The QUICK brown fox jumps over the lazy dog  
  
Function:   strncmp (first 10 characters only)  
Result:      String 1 is greater than string 2  
  
Function:   strnicmp _strnicmp (first 10 characters only)  
Result:      String 1 is equal to string 2  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica di stringhe](../../c-runtime-library/string-manipulation-crt.md)   
 [Impostazioni locali](../../c-runtime-library/locale.md)   
 [Interpretazione di sequenze di caratteri multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcmp, _mbsnbcmp_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_mbsnbicmp, _mbsnbicmp_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [Funzioni strcoll](../../c-runtime-library/strcoll-functions.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)