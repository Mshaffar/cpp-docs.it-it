---
title: _locking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _locking
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
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _locking
dev_langs:
- C++
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
caps.latest.revision: 19
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 7789a1634f5ee87d54d6b9f2aadbc720819f31ef
ms.contentlocale: it-it
ms.lasthandoff: 04/01/2017

---
# <a name="locking"></a>_locking
Blocca o sblocca i byte di un file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      int _locking(  
   int fd,  
   int mode,  
   long nbytes   
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `fd`  
 Descrittore di file.  
  
 *mode*  
 Azione di blocco da eseguire.  
  
 *nbytes*  
 Numero di byte da bloccare.  
  
## <a name="return-value"></a>Valore restituito  
 `_locking` restituisce 0 in caso di esito positivo. Il valore restituito-1 indica un errore, nel qual caso [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) è impostata su uno dei valori seguenti.  
  
 `EACCES`  
 Violazione del blocco (file già bloccato o sbloccato).  
  
 `EBADF`  
 Descrittore di file non valido.  
  
 `EDEADLOCK`  
 Violazione di blocco. Questo valore viene restituito quando è specificato il flag `_LK_LOCK` o `_LK_RLCK` e il file non può essere bloccato dopo 10 tentativi.  
  
 `EINVAL`  
 Argomento non valido passato a `_locking`.  
  
 Se l'errore è causato da un parametro non corretto, ad esempio un descrittore di file non valido, viene richiamato il gestore di parametri non validi, come descritto in [Convalida dei parametri](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Note  
 La funzione `_locking` blocca o sblocca *nbytes* byte del file specificato da `fd`. Il blocco di byte in un file impedisce l'accesso a tali byte da altri processi. Tutte le operazioni di blocco o sblocco iniziano dalla posizione corrente del puntatore del file e procedono per i successivi *nbytes* byte. È possibile bloccare byte oltre la fine del file.  
  
 L'argomento *mode* deve essere una delle seguenti costanti manifeste, definite in Locking.h.  
  
 `_LK_LOCK`  
 Blocca i byte specificati. Se i byte non possono essere bloccati, il programma ripeterà immediatamente il tentativo dopo 1 secondo. Se, dopo 10 tentativi, i byte non possono essere bloccati, la costante restituisce un errore.  
  
 `_LK_NBLCK`  
 Blocca i byte specificati. Se i byte non possono essere bloccati, la costante restituisce un errore.  
  
 `_LK_NBRLCK`  
 Uguale a `_LK_NBLCK`.  
  
 `_LK_RLCK`  
 Uguale a `_LK_LOCK`.  
  
 `_LK_UNLCK`  
 Sblocca i byte specificati, che devono essere stati bloccati in precedenza.  
  
 È possibile bloccare più aree di un file che non si sovrappongano. Un'area da sbloccare deve essere stata bloccata in precedenza. `_locking` non unisce aree adiacenti. Se due aree bloccate sono adiacenti, ogni area deve essere sbloccata separatamente. Le aree devono essere bloccate solo brevemente e devono essere sbloccate prima di chiudere un file o di uscire dal programma.  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|Intestazione facoltativa|  
|-------------|---------------------|---------------------|  
|`_locking`|\<io.h> e \<sys/locking.h>|\<errno.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md) nell'introduzione.  
  
## <a name="libraries"></a>Librerie  
 Tutte le versioni delle [librerie di runtime C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Esempio  
  
```  
// crt_locking.c  
/* This program opens a file with sharing. It locks  
 * some bytes before reading them, then unlocks them. Note that the  
 * program works correctly only if the file exists.  
 */  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/locking.h>  
#include <share.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
  
int main( void )  
{  
   int  fh, numread;  
   char buffer[40];  
  
   /* Quit if can't open file or system doesn't   
    * support sharing.   
    */  
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,   
                          _S_IREAD | _S_IWRITE );  
   printf( "%d %d\n", err, fh );  
   if( err != 0 )  
      exit( 1 );  
  
   /* Lock some bytes and read them. Then unlock. */  
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )  
   {  
      long lseek_ret;  
      printf( "No one can change these bytes while I'm reading them\n" );  
      numread = _read( fh, buffer, 30 );  
      buffer[30] = '\0';  
      printf( "%d bytes read: %.30s\n", numread, buffer );  
      lseek_ret = _lseek( fh, 0L, SEEK_SET );  
      _locking( fh, LK_UNLCK, 30L );  
      printf( "Now I'm done. Do what you will with them\n" );  
   }  
   else  
      perror( "Locking failed\n" );  
  
   _close( fh );  
}  
```  
  
## <a name="input-crtlockingtxt"></a>Input: crt_locking.txt  
  
```  
The first thirty bytes of this file will be locked.  
```  
  
## <a name="sample-output"></a>Esempio di output  
  
```  
No one can change these bytes while I'm reading them  
30 bytes read: The first thirty bytes of this  
Now I'm done. Do what you will with them  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di file](../../c-runtime-library/file-handling.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)