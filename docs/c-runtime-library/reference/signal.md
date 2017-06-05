---
title: signal | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- signal
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- signal
dev_langs:
- C++
helpviewer_keywords:
- signal function
ms.assetid: 094118de-d789-4063-b4f4-cffcc80bf29d
caps.latest.revision: 26
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
ms.openlocfilehash: b124479c62a62ef7795498b6c4a96191e2ecb6e4
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="signal"></a>signal
Imposta la gestione del segnale di interrupt.  
  
> [!IMPORTANT]
>  Non utilizzare questo metodo per interrompere un'applicazione [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)], eccetto che negli scenari di test o di debug. Le modalità dell'interfaccia utente o a livello di codice per chiudere un'app [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] non sono consentite in base a quanto indicato nella sezione 3.6 dei [Requisiti di certificazione delle app di Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Per altre informazioni, vedere [Ciclo di vita delle applicazioni (app di Windows Store)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Sintassi  
  
```  
void (__cdecl *signal(  
   int sig,   
   void (__cdecl *func ) (int [, int ] )))   
   (int);  
```  
  
#### <a name="parameters"></a>Parametri  
 `sig`  
 Valore del segnale.  
  
 `func`  
 Funzione da eseguire. Il primo parametro è un valore di segnale e il secondo parametro è un codice secondario che può essere usato quando il primo parametro è SIGFPE.  
  
## <a name="return-value"></a>Valore restituito  
 `signal` restituisce il valore precedente di `func` che è associato a un segnale specifico. Ad esempio, se il valore precedente di `func` era `SIG_IGN`, anche il valore restituito è `SIG_IGN`. Un valore restituito di `SIG_ERR` indica un errore; in tal caso `errno` è impostato su `EINVAL`.  
  
 Per altre informazioni sui codici restituiti, vedere [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Note  
 La funzione `signal` consente a un processo di scegliere uno dei vari modi per gestire un segnale di interrupt proveniente dal sistema operativo. L'argomento `sig` è l'interrupt a cui risponde `signal`; deve essere una delle seguenti costanti manifesto che sono definite in SIGNAL.H.  
  
|Valore di `sig`|Descrizione|  
|-----------------|-----------------|  
|`SIGABRT`|Terminazione anomala|  
|`SIGFPE`|Errore di virgola mobile|  
|`SIGILL`|Istruzione non valida|  
|`SIGINT`|Segnale CTRL+C|  
|`SIGSEGV`|Accesso all'archiviazione non valido|  
|`SIGTERM`|Richiesta di terminazione|  
  
 Se `sig` non è uno dei valori sopra indicati, viene richiamato il gestore di parametri non validi, come definito in [Convalida dei parametri](../../c-runtime-library/parameter-validation.md). Se l'esecuzione può continuare, la funzione imposta `errno` su`EINVAL` e restituisce `SIG_ERR`.  
  
 Per impostazione predefinita, `signal` termina il programma chiamante con codice di uscita 3, indipendentemente dal valore di `sig`.  
  
> [!NOTE]
>  `SIGINT` non è supportato per le applicazioni Win32. Quando si verifica un interrupt CTRL+C, i sistemi operativi Win32 generare un nuovo thread per gestire in maniera specifica l'interrupt. Ciò può far sì che un'applicazione a thread singolo, come una in UNIX, diventi multithreading e causi un comportamento imprevisto.  
  
 L'argomento `func` è un indirizzo per un gestore di segnale scritto dall'utente o per una delle costanti predefinite `SIG_DFL` o `SIG_IGN`, anch'esse definite in SIGNAL.H. Se `func` è una funzione, viene installata come gestore del segnale per il segnale specificato. Il prototipo del gestore di segnale richiede un solo argomento formale, `sig`, di tipo `int`. Il sistema operativo fornisce l'argomento effettivo tramite `sig` quando si verifica un interrupt. L'argomento è il segnale che ha generato l'interrupt. Pertanto, è possibile utilizzare le sei costanti manifesto (elencate nella tabella precedente) nel gestore di segnale per determinare quale interrupt si è verificato ed eseguire l'azione appropriata. Ad esempio, è possibile chiamare due volte `signal` per assegnare lo stesso gestore a due segnali diversi, quindi testare l'argomento `sig` nel gestore per eseguire azioni diverse in base al segnale ricevuto.  
  
 Durante i test per le eccezioni a virgola mobile (`SIGFPE`), `func` punta a una funzione che accetta un secondo argomento facoltativo corrispondente a una delle varie costanti manifeste definite in FLOAT.H nel formato `FPE_xxx`. Quando si verifica un segnale `SIGFPE`, è possibile testare il valore del secondo argomento per determinare il tipo di eccezione a virgola mobile e quindi eseguire l'azione appropriata. Questo argomento e i relativi valori possibili sono estensioni Microsoft.  
  
 Per le eccezioni a virgola mobile, il valore di `func` non viene reimpostato quando viene ricevuto il segnale. Per risolvere eccezioni a virgola mobile, utilizzare le clausole try/except per racchiudere le operazioni a virgola mobile. È anche possibile ricorrere a [setjmp](../../c-runtime-library/reference/setjmp.md) con [longjmp](../../c-runtime-library/reference/longjmp.md). In entrambi i casi, il processo chiamante riprende l'esecuzione e lascia che lo stato del processo a virgola mobile sia indefinito.  
  
 Se il gestore del segnale restituisce il controllo, il processo chiamante riprende l'esecuzione subito dopo il punto in cui ha ricevuto il segnale di interrupt. Ciò si verifica indipendentemente dal tipo di segnale o dalla modalità operativa.  
  
 Prima che venga eseguita la funzione specificata, il valore di `func` viene impostato su `SIG_DFL`. Il segnale di interrupt successivo viene gestito come descritto per `SIG_DFL`, se non specificato diversamente da una chiamata intermedia a `signal`. È possibile utilizzare questa funzionalità per reimpostare i segnali della funzione chiamata.  
  
 Dato che le routine del gestore di segnale vengono in genere chiamate in modo asincrono quando si verifica un'interrupt, la funzione del gestore di segnale può ottenere il controllo quando un'operazione di runtime è incompleta e in uno stato sconosciuto. Nell'elenco seguente sono riepilogate le restrizioni che determinano quali funzioni è possibile utilizzare nelle routine del gestore di segnale.  
  
-   Non eseguire le routine STDIO.H I/O o di basso livello (ad esempio, `printf` o `fread`).  
  
-   Non chiamare le routine dell'heap o qualsiasi routine che utilizzi le routine dell'heap, ad esempio `malloc`, `_strdup` o `_putenv`. Per altre informazioni, vedere [malloc](../../c-runtime-library/reference/malloc.md).  
  
-   Non utilizzare le funzioni che generano una chiamata di sistema (ad esempio, `_getcwd` o `time`).  
  
-   Non utilizzare `longjmp` a meno che l'interrupt non sia causato da un'eccezione a virgola mobile (ovvero, `sig` è `SIGFPE`). In questo caso, bisogna prima di tutto reinizializzare il pacchetto a virgola mobile utilizzando una chiamata a `_fpreset`.  
  
-   Non usare routine sostitutive.  
  
 Un programma deve contenere codice a virgola mobile se prevede di intercettare l'eccezione `SIGFPE` utilizzando la funzione. Se il programma non dispone di codice a virgola mobile e richiede il codice di gestione di segnale della libreria di runtime, è sufficiente dichiarare un double volatile e inizializzarlo su zero:  
  
`volatile double d = 0.0f;`  
  
 I segnali `SIGILL` e `SIGTERM` non vengono generati in Windows. Sono incluso per compatibilità con ANSI. È pertanto possibile impostare gestori di segnale per questi segnali usando `signal` e anche generare in modo esplicito questi segnali chiamando [raise](../../c-runtime-library/reference/raise.md).  
  
 Le impostazioni del segnale non vengono mantenute nei processi generati che sono stati creati dalle chiamate alle funzioni `_exec` o `_spawn`. Le impostazioni del segnale del nuovo processo vengono reimpostate sui valori predefiniti.  
  
## <a name="requirements"></a>Requisiti  
  
|Routine|Intestazione obbligatoria|  
|-------------|---------------------|  
|`signal`|\<signal.h>|  
  
 Per altre informazioni sulla compatibilità, vedere [Compatibilità](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo di `signal` per aggiungere un comportamento personalizzato al segnale `SIGABRT`. Per altre informazioni sul comportamento delle interruzioni, vedere [_set_abort_behavior](../../c-runtime-library/reference/set-abort-behavior.md).  
  
```cpp  
// crt_signal.c  
// compile with: /EHsc /W4  
// Use signal to attach a signal handler to the abort routine  
#include <stdlib.h>  
#include <signal.h>  
#include <tchar.h>  
  
void SignalHandler(int signal)  
{  
    if (signal == SIGABRT) {  
        // abort signal handler code  
    } else {  
        // ...  
    }  
}  
  
int main()  
{  
    typedef void (*SignalHandlerPointer)(int);  
  
    SignalHandlerPointer previousHandler;  
    previousHandler = signal(SIGABRT, SignalHandler);  
  
    abort();  
}  
```  
  
```Output  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo processo e ambiente](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [Funzioni _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_fpreset](../../c-runtime-library/reference/fpreset.md)   
 [Funzioni _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)