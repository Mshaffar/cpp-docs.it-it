---
title: "ccos, ccosf, ccosl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ccos"
  - "ccosf"
  - "ccosl"
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
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "ccos"
  - "ccosf"
  - "ccosl"
  - "complex/ccos"
  - "complex/ccosf"
  - "complex/ccosl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funzione ccos"
  - "funzione ccosf"
  - "funzione ccosl"
ms.assetid: 4ab936ac-ff85-49ac-9418-2b69cf5d4696
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# ccos, ccosf, ccosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera il coseno di un numero complesso.  
  
## Sintassi  
  
```  
_Dcomplex ccos(   
   _Dcomplex z   
);  
_Fcomplex ccos(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex ccos(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex ccosf(   
   _Fcomplex z   
);  
_Lcomplex ccosl(   
   _Lcomplex z   
);  
```  
  
#### Parametri  
 `z`  
 Un numero complesso che rappresenta l'angolo, espresso in radianti.  
  
## Valore restituito  
 Coseno di `z`, espresso in radianti.  
  
## Note  
 Dato che C\+\+ consente l'overload, è possibile chiamare degli overload di `ccos` che accettino e restituiscano valori `_Fcomplex` e `_Lcomplex`. In un programma C, `ccos` accetta e restituisce sempre un `_Dcomplex` valore.  
  
## Requisiti  
  
|Routine|Intestazione C|Intestazione C\+\+|  
|-------------|--------------------|------------------------|  
|`ccos`, `ccosf`, `ccosl`|\<complex.h\>|\< ccomplex \>|  
  
 Per altre informazioni sulla compatibilità, vedere la sezione [Compatibilità](../../c-runtime-library/compatibility.md) nell'introduzione.  
  
## Vedere anche  
 [Riferimento alfabetico alle funzioni](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh, catanhf, catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh, ctanhf, ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan, catanf, catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh, csinhf, csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh, casinhf, casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh, ccoshf, ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh, cacoshf, cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos, cacosf, cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [Ctan, ctanf, ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin, csinf, csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin, casinf, casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [csqrt, csqrtf, csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)