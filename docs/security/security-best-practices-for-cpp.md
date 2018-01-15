---
title: Le procedure consigliate per C++ | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: securitybestpracticesVC
dev_langs: C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
caps.latest.revision: "45"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f1474f44b81a95c119a405dda8a91db62a08417
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2018
---
# <a name="security-best-practices-for-c"></a>Procedure di sicurezza consigliate per C++
Questo articolo contiene informazioni su strumenti e procedure di sicurezza. Il loro uso non rende le applicazioni immuni da attacchi, ma riduce le probabilità che un attacco abbia successo.  
  
## <a name="visual-c-security-features"></a>Funzionalità di sicurezza di Visual C++  
 Queste funzionalità di sicurezza sono incluse nel compilatore e nel linker di Visual C++:  
  
 [/guard (abilita guard flusso di controllo)](../build/reference/guard-enable-control-flow-guard.md)  
 Fa in modo che il compilatore analizzi il flusso di controllo per verificare la presenza di destinazioni di chiamata indiretta in fase di compilazione e che quindi inserisca il codice per verificare le destinazioni in fase di esecuzione.  
  
 [/GS (controllo sicurezza buffer)](../build/reference/gs-buffer-security-check.md)  
 Indica al compilatore di inserire il codice di rilevamento di sovraccarico nelle funzioni esposte al rischio di exploit. Quando viene rilevato un sovraccarico, l'esecuzione viene interrotta. Per impostazione predefinita, questa opzione è attivata.  
  
 [/SAFESEH (l'immagine ha gestori delle eccezioni sicuri)](../build/reference/safeseh-image-has-safe-exception-handlers.md)  
 Indica al linker di includere nell'immagine di output una tabella contenente l'indirizzo di ogni gestore di eccezioni. In fase di esecuzione, il sistema operativo usa la tabella per verificare che vengano eseguiti solo i gestori di eccezione legittimi. Questo consente di evitare l'esecuzione di gestori di eccezione introdotti da un attacco dannoso in fase di esecuzione. Per impostazione predefinita, questa opzione è impostata su OFF.  
  
 [/NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (compatibile con protezione esecuzione programmi)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)  
 Queste opzioni del compilatore e del linker consentono la compatibilità con Protezione esecuzione programmi. Protezione esecuzione programmi protegge la CPU dall'esecuzione di pagine non di codice.  
  
 [/analyze (analisi codice)](../build/reference/analyze-code-analysis.md)  
 Questa opzione del compilatore attiva l'analisi codice che segnala i potenziali problemi di sicurezza, ad esempio sovraccarico del buffer, memoria non inizializzata, dereferenziazione puntatore Null e perdite di memoria. Per impostazione predefinita, questa opzione è impostata su OFF. Per ulteriori informazioni, vedere [analisi del codice per C/C++ Panoramica](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
 [/DYNAMICBASE (uso della funzionalità ASLR)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)  
 Questa opzione del linker consente la compilazione di un'immagine eseguibile che può essere caricata in posizioni diverse in memoria all'inizio dell'esecuzione. Questa opzione rende inoltre il percorso dello stack in memoria molto meno prevedibile.  
  
## <a name="security-enhanced-crt"></a>CRT con sicurezza avanzata  
 La libreria di runtime C (CRT) è stata ampliata per poter includere le versioni sicure delle funzioni che comportano rischi per la sicurezza, ad esempio la funzione di copia stringa `strcpy` non controllata. Le versioni precedenti non sicure di queste funzioni, essendo deprecate, generano avvisi in fase di compilazione. Si consiglia di usare le versioni sicure di queste funzioni CRT invece di eliminare gli avvisi di compilazione. Per altre informazioni, vedere [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="safeint-library"></a>Libreria SafeInt  
 [Libreria SafeInt](../windows/safeint-library.md) consente di evitare gli overflow di integer e altri errori che potrebbero verificarsi durante l'applicazione esegue operazioni matematiche. Il `SafeInt` libreria include il [SafeInt (classe)](../windows/safeint-class.md), [classe SafeIntException](../windows/safeintexception-class.md)e diversi [funzioni SafeInt](../windows/safeint-functions.md).  
  
 La classe `SafeInt` protegge da exploit basati sugli overflow di Integer e sulle divisioni per zero. È possibile usarla per gestire i confronti tra valori di tipi diversi. Fornisce due criteri di gestione degli errori. Il criterio predefinito è per la classe `SafeInt` che genera un'eccezione della classe `SafeIntException` che segnala perché un'operazione matematica non può essere completata. Il secondo criterio è per la classe `SafeInt` che interrompe l'esecuzione del programma. È inoltre possibile definire un criterio personalizzato.  
  
 Ogni funzione `SafeInt` protegge un'operazione matematica da un errore sfruttabile. È possibile usare due diversi generi di parametri senza convertirli nello stesso tipo. Per proteggere più operazioni matematiche, usare la classe `SafeInt`.  
  
## <a name="checked-iterators"></a>Iteratori verificati  
 Un iteratore verificato applica i limiti del contenitore. Per impostazione predefinita, quando un iteratore verificato è fuori limite, genera un'eccezione e termina l'esecuzione del programma. Un iteratore verificato fornisce altri livelli di risposta che dipendono dai valori assegnati al preprocessore, ad esempio  **\_sicura\_SCL\_GENERA** e  **\_ITERATORE\_DEBUG\_livello**. Ad esempio, in  **\_ITERATORE\_DEBUG\_LEVEL = 2**, un iteratore verificato fornisce controlli di correttezza completi in modalità debug, che vengono resi disponibili tramite le asserzioni. Per ulteriori informazioni, vedere [iteratori](../standard-library/checked-iterators.md) e [ \_ITERATORE\_DEBUG\_livello](../standard-library/iterator-debug-level.md).  
  
## <a name="code-analysis-for-managed-code"></a>Analisi del codice gestito  
 L'analisi del codice gestito, nota anche come FxCop, controlla la conformità degli assembly alle linee guida di progettazione di .NET Framework. FxCop analizza il codice e i metadati in ogni assembly per verificare la presenza di difetti nelle aree seguenti:  
  
-   Progettazione di librerie  
  
-   Localizzazione  
  
-   Convenzioni di denominazione  
  
-   Prestazioni  
  
-   Sicurezza  
  
## <a name="windows-application-verifier"></a>Windows Application Verifier  
 Application Verifier (AppVerifier) aiuta a identificare i potenziali problemi di compatibilità, stabilità e sicurezza delle applicazioni.  
  
 AppVerifier monitora come un'applicazione usa il sistema operativo. Controlla il file system, il Registro di sistema, la memoria e le API mentre l'applicazione è in esecuzione e suggerisce le correzioni del codice sorgente per i problemi rilevati.  
  
 È possibile usare AppVerifier per:  
  
-   Testare i potenziali errori di compatibilità delle applicazioni causati da comuni sbagli commessi durante la programmazione.  
  
-   Cercare in un'applicazione problemi relativi alla memoria.  
  s
-   Identificare potenziali problemi di sicurezza in un'applicazione.  
  
 AppVerifier fa parte di Application Compatibility Toolkit, è disponibile il [compatibilità delle applicazioni](http://go.microsoft.com/fwlink/p/?linkid=91277) sul sito web TechNet.  
  

## <a name="windows-user-accounts"></a>Account utente di Windows  
 L'uso di account utente di Windows appartenenti al gruppo Administrators espone gli sviluppatori e, per estensione, i clienti a rischi per la sicurezza. Per ulteriori informazioni, vedere [in esecuzione come membro del gruppo di utenti](running-as-a-member-of-the-users-group.md) e [applicazione influisce sulla modalità controllo Account utente (UAC)](how-user-account-control-uac-affects-your-application.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Security>   
 [Sicurezza](/dotnet/standard/security/index)   
 [Effetti del Controllo dell'account utente sull'applicazione](how-user-account-control-uac-affects-your-application.md)