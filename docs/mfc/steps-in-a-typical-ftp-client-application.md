---
title: I passaggi in un'applicazione Client FTP tipica | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d707d2b4903394b6b3b70367184767cce28ea1d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Passaggi in un'applicazione client FTP tipica
Crea un'applicazione client FTP tipica un [CInternetSession](../mfc/reference/cinternetsession-class.md) e [CFtpConnection](../mfc/reference/cftpconnection-class.md) oggetto. Si noti che queste classi WinInet MFC non controllano effettivamente le impostazioni proxy del tipo; IIS non.  
  
 Inoltre, vedere gli articoli della Knowledge Base:  
  
-   Procedura: FTP con Proxy basato su CERN mediante l'API WinInet (ID articolo: Q166961)  
  
-   ESEMPIO: FTP con Password basati su CERN protetto Proxy (ID articolo: Q216214)  
  
-   Manager non riesce a visualizzare i servizi Proxy installato di servizi Internet (ID articolo: Q216802)  
  
 Nella tabella seguente vengono illustrati i passaggi che è possibile eseguire in un'applicazione client FTP tipica.  
  
|Obiettivo|Azioni da effettuare|Effetti|  
|---------------|----------------------|-------------|  
|Avviare una sessione FTP.|Creare un [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Inizializza WinInet e si connette al server.|  
|Connettersi a un server FTP.|Utilizzare [CInternetSession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Restituisce un [CFtpConnection](../mfc/reference/cftpconnection-class.md) oggetto.|  
|Passare a una nuova directory FTP sul server.|Utilizzare [CFtpConnection:: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Modifica la directory a cui si è attualmente connessi sul server.|  
|Individuare il primo file nella directory FTP.|Utilizzare [CFtpFileFind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Trova il primo file. Restituisce FALSE se non viene trovato alcun file.|  
|Individuare il file successivo nella directory FTP.|Utilizzare [CFtpFileFind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Individua il file successivo. Restituisce FALSE se il file non viene trovato.|  
|Aprire il file trovato da **FindFile** o `FindNextFile` per la lettura o scrittura.|Utilizzare [CFtpConnection:: OpenFile](../mfc/reference/cftpconnection-class.md#openfile), utilizzando il nome del file restituito da [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) o [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Apre il file nel server per la lettura o scrittura. Restituisce un [CInternetFile](../mfc/reference/cinternetfile-class.md) oggetto.|  
|Leggere o scrivere nel file.|Utilizzare [CInternetFile:: Read](../mfc/reference/cinternetfile-class.md#read) o [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|Legge o scrive il numero specificato di byte, usando un buffer che è fornire.|  
|Gestire le eccezioni.|Utilizzare il [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gestisce tutti i tipi di eccezioni comuni di Internet.|  
|Terminare la sessione FTP.|Smaltire la [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Effettua la pulizia automatica degli handle e delle connessioni del file aperto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Prerequisiti per le classi Client Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Scrittura di un'applicazione client Internet con classi WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)