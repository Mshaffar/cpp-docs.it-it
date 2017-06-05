---
title: "Convenzioni di chiamata, parametri e tipo restituito | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "convenzioni di chiamata, funzioni di supporto"
  - "funzioni di supporto, convenzioni di chiamata"
  - "funzioni di supporto, tipi restituiti"
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Convenzioni di chiamata, parametri e tipo restituito
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Il prototipo della routine dell'helper è:  
  
```  
FARPROC WINAPI __delayLoadHelper2(   
   PCImgDelayDescr pidd,  
   FARPROC * ppfnIATEntry  
);  
```  
  
 dove:  
  
 `pidd`  
 Un puntatore `const` a `ImgDelayDescr` \(vedere delayimp.h\) che contiene gli offset di vari dati relativi all'importazione, un timestamp per le informazioni di associazione e un set di attributi che forniscono ulteriori informazioni sul contenuto del descrittore.  Attualmente esiste un solo attributo, `dlattrRva`, che indica che gli indirizzi del descrittore sono indirizzi virtuali relativi \(in contrapposizione a indirizzi virtuali\).  
  
 Per la definizione della struttura di `PCImgDelayDescr`, vedere [Struttura e definizioni di costanti](../../build/reference/structure-and-constant-definitions.md).  
  
 `ppfnIATEntry`  
 Un puntatore allo slot nella tabella di indirizzi di importazione a caricamento ritardato da aggiornare con l'indirizzo della funzione importata.  Nella routine dell'helper deve essere archiviato lo stesso valore che verrà restituito in questa posizione.  
  
## Valori restituiti previsti  
 Se la funzione ha esito positivo, restituisce l'indirizzo della funzione importata.  
  
 Se ha esito negativo, genera un'eccezione e restituisce 0.  Possono essere generati tre tipi di eccezioni:  
  
-   Parametro non valido, se gli attributi in `pidd` non sono specificati correttamente.  
  
-   `LoadLibrary`: impossibile leggere la DLL specificata.  
  
-   Errore di `GetProcAddress`.  
  
 È responsabilità dell'utente gestire queste eccezioni.  
  
## Note  
 La convenzione di denominazione per la funzione helper è `__stdcall`.  Il tipo del valore restituito non è rilevante, pertanto viene usato FARPROC.  Questa funzione ha un collegamento C.  
  
 Il valore restituito dell'helper a caricamento ritardato deve essere archiviato nel percorso del puntatore della funzione passata, a meno che non si desideri che la routine dell'helper non venga usata come un hook di notifica.  In questo caso, il codice è responsabile dell'individuazione del puntatore funzione appropriato da restituire.  Il codice thunk generato dal linker accetta quindi quel valore restituito come destinazione effettiva dell'importazione e passa direttamente ad essa.  
  
## Esempio  
 Nel codice seguente viene illustrato come implementare una semplice funzione hook.  
  
```  
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)  
{  
    switch (dliNotify) {  
        case dliStartProcessing :  
  
            // If you want to return control to the helper, return 0.  
            // Otherwise, return a pointer to a FARPROC helper function  
            // that will be used instead, thereby bypassing the rest   
            // of the helper.  
  
            break;  
  
        case dliNotePreLoadLibrary :  
  
            // If you want to return control to the helper, return 0.  
            // Otherwise, return your own HMODULE to be used by the   
            // helper instead of having it call LoadLibrary itself.  
  
            break;  
  
        case dliNotePreGetProcAddress :  
  
            // If you want to return control to the helper, return 0.  
            // If you choose you may supply your own FARPROC function   
            // address and bypass the helper's call to GetProcAddress.  
  
            break;  
  
        case dliFailLoadLib :   
  
            // LoadLibrary failed.  
            // If you don't want to handle this failure yourself, return 0.  
            // In this case the helper will raise an exception   
            // (ERROR_MOD_NOT_FOUND) and exit.  
            // If you want to handle the failure by loading an alternate   
            // DLL (for example), then return the HMODULE for   
            // the alternate DLL. The helper will continue execution with   
            // this alternate DLL and attempt to find the  
            // requested entrypoint via GetProcAddress.  
  
            break;  
  
        case dliFailGetProc :  
  
            // GetProcAddress failed.  
            // If you don't want to handle this failure yourself, return 0.  
            // In this case the helper will raise an exception   
            // (ERROR_PROC_NOT_FOUND) and exit.  
            // If you choose you may handle the failure by returning   
            // an alternate FARPROC function address.  
  
            break;  
  
        case dliNoteEndProcessing :   
  
            // This notification is called after all processing is done.   
            // There is no opportunity for modifying the helper's behavior  
            // at this point except by longjmp()/throw()/RaiseException.   
            // No return value is processed.  
  
            break;  
  
        default :  
  
            return NULL;  
    }  
  
    return NULL;  
}  
  
/*   
and then at global scope somewhere  
PfnDliHook __pfnDliNotifyHook2 = delayHook;  
*/  
```  
  
## Vedere anche  
 [Informazioni sulla funzione di supporto](../../build/reference/understanding-the-helper-function.md)