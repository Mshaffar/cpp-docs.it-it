---
title: Tipo di accesso alla raccolta | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 8f05738c02fd70fde5fc2d92c5ee1e823747797c
ms.contentlocale: it-it
ms.lasthandoff: 10/09/2017

---
# <a name="type-library-access"></a>Accesso alla libreria dei tipi
Librerie dei tipi espongono le interfacce di un controllo OLE ad altre applicazioni compatibili con OLE. Ogni controllo OLE deve avere una libreria dei tipi, se una o più interfacce da esporre.  
  
 Le macro seguenti consentono un controllo OLE fornire l'accesso alla propria libreria dei tipi:  
  
### <a name="type-library-access"></a>Accesso alla libreria dei tipi  
  
|||  
|-|-|  
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Dichiara un `GetTypeLib` funzione membro di un controllo OLE (deve essere utilizzato nella dichiarazione di classe).|  
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementa un `GetTypeLib` funzione membro di un controllo OLE (che sarà utilizzata nell'implementazione della classe).|  
  
##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB  
 Dichiara il `GetTypeLib` funzione membro di classe del controllo.  
  
```   
DECLARE_OLETYPELIB(class_name)   
```  
  
### <a name="parameters"></a>Parametri  
 *CLASS_NAME*  
 Il nome della classe del controllo correlata alla libreria dei tipi.  
  
### <a name="remarks"></a>Note  
 Utilizzare questa macro nel file di intestazione della classe di controllo.  

### <a name="requirements"></a>Requisiti  
 **Intestazione:** afxdisp.h  

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB  
 Implementa il controllo `GetTypeLib` funzione membro.  
  
```   
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)   
```  
  
### <a name="parameters"></a>Parametri  
 *CLASS_NAME*  
 Il nome della classe del controllo correlata alla libreria dei tipi.  
  
 *tlid*  
 Il numero ID della libreria dei tipi.  
  
 `wVerMajor`  
 Il numero di versione principale della libreria di tipo.  
  
 `wVerMinor`  
 Il numero di versione secondaria della libreria di tipo.  
  
### <a name="remarks"></a>Note  
 Questa macro deve essere presente nel file di implementazione per qualsiasi classe di controllo che usa il `DECLARE_OLETYPELIB` (macro).  

### <a name="requirements"></a>Requisiti  
 **Intestazione:** afxdisp.h  
   
## <a name="see-also"></a>Vedere anche  
 [Macro e funzioni globali](../../mfc/reference/mfc-macros-and-globals.md)
