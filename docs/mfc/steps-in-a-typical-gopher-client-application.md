---
title: I passaggi in un'applicazione Client Gopher tipica | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5108e997336e53434ad33030c0e79be027aa4a98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Passaggi in un'applicazione client gopher tipica
Nella tabella seguente vengono illustrati i passaggi che è possibile eseguire in un'applicazione client gopher tipica.  
  
|Obiettivo|Azioni da effettuare|Effetti|  
|---------------|----------------------|-------------|  
|Avviare la sessione gopher.|Creare un [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Inizializza WinInet e si connette al server.|  
|Connettersi a un server gopher.|Utilizzare [CInternetSession:: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Restituisce un [CGopherConnection](../mfc/reference/cgopherconnection-class.md) oggetto.|  
|Trovare la prima risorsa nel gopher.|Utilizzare [CGopherFileFind:: FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Trova il primo file. Restituisce FALSE se non viene trovato alcun file.|  
|Trovare la risorsa successiva nel gopher.|Utilizzare [CGopherFileFind:: FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Individua il file successivo. Restituisce FALSE se il file non viene trovato.|  
|Aprire il file trovato da **FindFile** o `FindNextFile` per la lettura.|Ottenere un indicatore di posizione gopher utilizzando [CGopherFileFind:: GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Utilizzare [CGopherConnection:: OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Apre il file specificato dall'indicatore di posizione. `OpenFile`Restituisce un [CGopherFile](../mfc/reference/cgopherfile-class.md) oggetto.|  
|Aprire un file utilizzando un indicatore di posizione gopher che è fornire.|Creare un localizzatore gopher utilizzando [CGopherConnection:: CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Utilizzare [CGopherConnection:: OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Apre il file specificato dall'indicatore di posizione. `OpenFile`Restituisce un [CGopherFile](../mfc/reference/cgopherfile-class.md) oggetto.|  
|Leggere il file.|Utilizzare [CGopherFile](../mfc/reference/cgopherfile-class.md).|Legge il numero specificato di byte, usando un buffer che è fornire.|  
|Gestire le eccezioni.|Utilizzare il [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gestisce tutti i tipi di eccezioni comuni di Internet.|  
|Terminare la sessione gopher.|Smaltire la [CInternetSession](../mfc/reference/cinternetsession-class.md) oggetto.|Effettua la pulizia automatica degli handle e delle connessioni del file aperto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Prerequisiti per le classi Client Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Scrittura di un'applicazione client Internet con classi WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)