---
title: Distribuzione di Universal CRT | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20006118d4bf27c379b78b84dc8807a4fd6c5e6c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34256290"
---
# <a name="universal-crt-deployment"></a>Distribuzione di Universal CRT

Da Visual Studio .NET a Visual Studio 2013, ogni versione principale del compilatore e degli strumenti C++ includeva una nuova versione autonoma della libreria di runtime C (CRT) di Microsoft. Queste versioni autonome della libreria CRT erano indipendenti l'una dall'altra e, a vari livelli, erano incompatibili tra loro. La libreria CRT, ad esempio, usata da Visual Studio 2012, corrispondeva alla versione 11, denominata msvcr110.dll, e la libreria CRT usata da Visual Studio 2013 corrispondeva alla versione 12, denominata msvcr120.dll. A partire da Visual Studio 2015, questo non avviene più. Visual Studio 2015 e le versioni successive di Visual Studio usano tutte una sola libreria Universal CRT.

La libreria Universal CRT è un componente del sistema operativo Microsoft Windows, è inclusa come parte del sistema operativo in Windows 10 ed è disponibile per i sistemi operativi precedenti, da Windows Vista a Windows 8.1, tramite Windows Update. La distribuzione locale della libreria Universal CRT è supportata, con alcune restrizioni.

## <a name="central-deployment"></a>Distribuzione centrale

Il metodo preferito per l'installazione centrale di Universal CRT consiste nell'uso di Microsoft Windows Update. Universal CRT è un aggiornamento consigliato per tutti i sistemi operativi Microsoft Windows supportati che viene quindi installato per impostazione predefinita dalla maggior parte dei computer nell'ambito del processo di aggiornamento normale. La versione iniziale di Universal CRT era la [KB2999226](https://support.microsoft.com/en-us/kb/2999226). Successivamente è stato creato un aggiornamento con varie correzioni di bug con numero di versione [KB3118401](https://support.microsoft.com/en-us/kb/3118401). Ci sono stati altri aggiornamenti con altre correzioni di bug e nuove funzionalità. For aggiornamenti più recenti, cercare Universal C Runtime o Universal CRT, in [support.microsoft.com](https://support.microsoft.com).

Non tutti i computer Microsoft Windows installano regolarmente gli aggiornamenti tramite Windows Update e in alcuni potrebbero non essere installati tutti gli aggiornamenti consigliati. Per supportare l'uso di applicazioni compilate tramite i set di strumenti C++ di Visual Studio 2015 e versioni successive in tali computer, sono disponibili componenti ridistribuibili Universal CRT per la distribuzione offline. Tali componenti ridistribuibili possono essere scaricati da uno dei collegamenti KB sopra riportati. Si noti che i componenti ridistribuibili Universal CRT richiedono che il computer sia stato aggiornato al Service Pack corrente. Il componente ridistribuibile per Windows 7, ad esempio, può essere installato solo in Windows 7 SP1, non in Windows 7 RTM.

Poiché la libreria Universal CRT è una dipendenza fondamentale delle librerie C++, Visual C++ Redistributable (VCRedist) installa una versione di base della libreria Universal CRT nei computer in cui questa non è ancora stata installata, in modo da soddisfare le dipendenze delle librerie C++. Se l'applicazione dipende da una versione più recente della libreria Universal CRT, è necessario installare tale versione in modo esplicito. È consigliabile installarla prima di VCRedist, per evitare di dover eventualmente riavviare più volte il computer.

## <a name="local-deployment"></a>Distribuzione locale

La distribuzione locale della libreria Universal CRT è supportata ma non consigliata per motivi di prestazioni e di sicurezza.  Le DLL per la distribuzione locale sono incluse in Windows SDK, nella subdirectory Windows Kits\\10\\Redist\\ucrt\\DLLs, per architettura. Le DLL necessarie includono ucrtbase.dll e un set di DLL di inoltro APISet denominato api-ms-win-\*.dll. Il set di DLL necessario in ogni sistema operativo varia. Quando si esegue la distribuzione locale, quindi, è consigliabile includere tutte le DLL.

Ci sono due limitazioni alla distribuzione locale da tenere presenti:

- In Windows 10, viene sempre usata la libreria Universal CRT nella directory di sistema, anche se una copia di tale libreria è inclusa in una cartella locale dell'applicazione. Questo avviene anche se la copia locale di Universal CRT è più recente, poiché la libreria Universal CRT in Windows 10 è un componente di base del sistema operativo.

- Nelle versioni di Windows precedenti a Windows 8, non è possibile includere la libreria Universal CRT in un pacchetto locale con un plug-che si trova in una directory diversa da quella contenente l'eseguibile principale dell'app. In questo caso, le DLL di inoltro APISet non sono in grado di risolvere correttamente ucrtbase.dll. Ecco alcune soluzioni alternative consigliate:

  - Collegare la libreria Universal CRT in modo statico
  - Distribuire centralmente la libreria Universal CRT
  - Inserire i file della libreria Universal CRT nella stessa directory dell'app.

## <a name="deployment-on-microsoft-windows-xp"></a>Distribuzione in Microsoft Windows XP

Visual Studio 2015 e Visual Studio 2017 continuano a supportare lo sviluppo di software per Microsoft Windows XP. Per consentire tale supporto, una versione della libreria Universal CRT funziona in Microsoft Windows XP. Il sistema operativo Microsoft Windows XP non gode più del supporto Mainstream né del supporto Extended. La distribuzione centrale della libreria Universal CRT in Microsoft Windows XP è pertanto diversa da altri sistemi operativi.

Quando viene installato in Windows XP, Visual C++ Redistributable installa direttamente la libreria Universal CRT e tutte le sue dipendenze nella directory di sistema, senza installare aggiornamenti da Windows Update e senza dipendere da questi. I modelli unione ridistribuibili, i file Microsoft_VC*versione*_CRT_\*.msm, si comportano allo stesso modo.

La distribuzione locale di Universal CRT in Windows XP è la stessa di altri sistemi operativi supportati.

## <a name="see-also"></a>Vedere anche

- [Distribuzione in Visual C++](deployment-in-visual-cpp.md)