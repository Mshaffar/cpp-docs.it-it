---
title: "mbsinit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbsinit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbsinit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mbsinit (funzione)"
ms.assetid: 4618555b-baaa-4d04-93fa-36abae411034
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# mbsinit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Tiene traccia dello stato di conversione di caratteri multibyte.  
  
## Sintassi  
  
```  
  
      int mbsinit(  
   const mbstate_t* ps  
);  
```  
  
#### Parametri  
 `ps`  
 Un puntatore ad una variabile [mbstate\_t](../../c-runtime-library/standard-types.md).  
  
## Valore restituito  
 Diverso da zero se `ps` è NULL o se non è al centro di una conversione.  
  
## Note  
 Quando si utilizza uno dei metodi ANSI che accetta un puntatore **mbstate\_t** , passando l'indirizzo del `mbstate_t` questa ritornerà le informazioni sulla conversione dell'ultimo byte nel buffer.  
  
 La tabella codici appropriata deve essere installata per supportare i caratteri multibyte.  
  
## Esempio  
  
```  
// crt_mbsinit.cpp  
#include <stdio.h>  
#include <mbctype.h>  
#include <string.h>  
#include <locale.h>  
#include <cwchar>  
#include <xlocinfo.h>  
  
#define   BUF_SIZE   0x40  
  
wchar_t      g_wcBuf[BUF_SIZE] = L"This a wc buffer that will be over written...";  
char      g_mbBuf[BUF_SIZE] = "AaBbCc\x9A\x8B\xE0\xEF\xF0xXyYzZ";  
int      g_nInit = strlen(g_mbBuf);  
  
int MbsinitSample(char* szIn, wchar_t* wcOut, int nMax)  
{  
   mbstate_t   state = {0};  
   size_t      nConvResult, nmbLen = 0, nwcLen = 0;  
   wchar_t*   wcCur = wcOut;  
   wchar_t*   wcEnd = wcCur + nMax;  
   const char*   mbCur = szIn;  
   const char*   mbEnd = mbCur + strlen(mbCur) + 1;  
   char*      szLocal = setlocale(LC_ALL, "japanese");  
  
   printf("Locale set to: \"%s\"\n", szLocal);  
  
   if   (_setmbcp(_MB_CP_LOCALE) != -1)  
   {  
      while   ((mbCur < mbEnd) && (wcCur < wcEnd))  
      {  
         nConvResult = mbrtowc(wcCur, mbCur, 1, &state);   
  
         switch   (nConvResult)  
         {  
            case 0:  
            {   // done  
               printf("Conversion succeeded!\nMB String: ");  
               printf(szIn);  
               printf("\nWC String: ");  
               wprintf(wcOut);  
               printf("\n");  
               mbCur = mbEnd;  
               break;  
            }  
  
            case -1:  
            {   // encoding error  
               printf("ERROR: The call to mbrtowc has detected an encoding error.\n");  
               mbCur = mbEnd;  
               break;  
            }  
  
            case -2:  
            {   // incomplete character  
               if   (!mbsinit(&state))  
               {  
                  printf("Currently in middle of mb conversion, state = %x\n", state);  
                  // state will contain data regarding lead byte of mb character  
               }  
  
               ++nmbLen;  
               ++mbCur;  
               break;  
            }  
  
            default:  
            {  
               if   (nConvResult > 2)   // Microsoft mb should never be larger than 2  
                  printf("ERROR: nConvResult = %d\n", nConvResult);  
  
               ++nmbLen;  
               ++nwcLen;  
               ++wcCur;  
               ++mbCur;  
               break;  
            }  
         }  
      }  
   }  
   else  
      printf("ERROR: _setmbcp(932) failed!");  
  
   return 0;  
}  
  
int main(int argc, char* argv[])  
{  
   return MbsinitSample(g_mbBuf, g_wcBuf, BUF_SIZE);  
}  
```  
  
## Esempio di output  
  
```  
Locale set to: "Japanese_Japan.932"  
Currently in middle of mb conversion, state = 9a  
Currently in middle of mb conversion, state = e0  
Currently in middle of mb conversion, state = f0  
Conversion succeeded!  
MB String: AaBbCcxXyYzZ  
WC String: AaBbCcxXyYzZ  
```  
  
## Vedere anche  
 [Classificazione per byte](../../c-runtime-library/byte-classification.md)