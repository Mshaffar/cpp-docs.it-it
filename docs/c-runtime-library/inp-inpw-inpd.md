---
title: _inp, _inpw, _inpd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs:
- C++
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: ec0c11cf43080389363fc682aad9511a958e6edd
ms.contentlocale: it-it
ms.lasthandoff: 04/01/2017

---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd
Restituisce, da una porta, un byte (`_inp`), una parola (`_inpw`) o una parola doppia (`_inpd`).  
  
> [!IMPORTANT]
>  Queste funzioni sono obsolete. A partire da Visual Studio 2015 non sono disponibili in CRT.  
  
> [!IMPORTANT]
>  Non è possibile usare questa API nelle applicazioni eseguite in Windows Runtime. Per altre informazioni, vedere l'articolo relativo alle [funzioni CRT non supportate con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintassi  
  
```  
int _inp(   
   unsigned short port   
);  
unsigned short _inpw(   
   unsigned short port   
);  
unsigned long _inpd(   
   unsigned short port   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `port`  
 Numero porta di I/O.  
  
## <a name="return-value"></a>Valore restituito  
 Le funzioni restituiscono il byte, la parola o la parola doppia letti da `port`. Non vi è restituzione di errori.  
  
## <a name="remarks"></a>Osservazioni  
 Le funzioni `_inp`, `_inpw`e `_inpd` leggono un byte, una parola e una doppia parola, rispettivamente, dalla porta di input specificata. Il valore di input può essere qualsiasi Unsigned Short Integer nell'intervallo compreso tra 0 e 65.535.  
  
 Dal momento che queste funzioni leggono direttamente da una porta di I/O, potrebbero non essere usate nel codice utente in Windows NT, Windows 2000, Windows XP e Windows Server 2003.  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`_inp`|\<conio.h>|  
|`_inpw`|\<conio.h>|  
|`_inpd`|\<conio.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibility](../c-runtime-library/compatibility.md) (Compatibilità).  
  
## <a name="libraries"></a>Librerie  
 Tutte le versioni delle [librerie di runtime C](../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Console e porta I/O](../c-runtime-library/console-and-port-i-o.md)   
 [_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)