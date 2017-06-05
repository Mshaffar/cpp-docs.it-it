---
title: Class factory e licenze | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories, and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 3d045736f9a54d344c67e3f7408198e65a0bc95f
ms.openlocfilehash: 17a99edadeb7a5bd923126bce7fbef50313e1867
ms.contentlocale: it-it
ms.lasthandoff: 03/29/2017

---
# <a name="class-factories-and-licensing"></a>Class factory e licenze
Per creare un'istanza del controllo OLE, un'applicazione contenitore chiama una funzione membro della factory di classe del controllo. Poiché il controllo è un oggetto OLE effettivo, la class factory è responsabile per la creazione di istanze del controllo. Ogni classe del controllo OLE deve avere una class factory.  
  
 Un'altra caratteristica importante di controlli OLE è la capacità di applicare una licenza. La creazione guidata controllo consente di integrare gestione licenze durante la creazione del progetto di controllo. Per ulteriori informazioni sulla licenza di controllo, vedere l'articolo [controlli ActiveX: gestione delle licenze di un controllo ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 Nella tabella seguente sono elencate diverse macro e funzioni utilizzate per dichiarare e implementare una factory di classe del controllo e di licenza del controllo.  
  
### <a name="class-factories-and-licensing"></a>Class factory e licenze  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Dichiara la class factory per una pagina di proprietà o controllo OLE.|  
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementa il controllo `GetClassID` funzione e viene dichiarata un'istanza della class factory.|  
|[BEGIN_OLEFACTORY](#begin_olefactory)|Inizia la dichiarazione di tutte le funzioni di gestione delle licenze.|  
|[END_OLEFACTORY](#end_olefactory)|Termina la dichiarazione di tutte le funzioni di gestione delle licenze.|  
|[AfxVerifyLicFile](#afxverifylicfile)|Verifica se un controllo viene concesso in licenza in un computer specifico.|  
  
##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX  
 Dichiara una class factory e `GetClassID` funzione membro di classe del controllo.  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>Parametri  
 *CLASS_NAME*  
 Il nome della classe del controllo.  
  
### <a name="remarks"></a>Note  
 Utilizzare questa macro in file di intestazione di classe del controllo per un controllo che non supportano la gestione licenze.  
  
 Si noti che questa macro viene utilizzato lo stesso scopo di esempio di codice seguente:  
  
 [!code-cpp[NVC_MFCAxCtl #14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxctl. h  
  
##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX  
 Implementa una factory di classe del controllo e [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) funzione membro di classe del controllo.  
  
```   
IMPLEMENT_OLECREATE_EX(
   class_name,   
    external_name,    
    l,   
    w1,   
    w2,   
    b1,   
    b2,   
    b3,   
    b4,   
    b5,   
    b6,   
    b7,
    b8)   
```  
  
### <a name="parameters"></a>Parametri  
 *CLASS_NAME*  
 Il nome della classe di proprietà del controllo pagina.  
  
 *external_name*  
 Il nome dell'oggetto esposto alle applicazioni.  
  
 *l, s1, S2, b1, b2, b3, b4, b5, b6, b7, b8*  
 Componenti della classe **CLSID**. Per ulteriori informazioni su questi parametri, vedere la sezione Osservazioni per [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).  
  
### <a name="remarks"></a>Note  
 Questa macro deve essere presente nel file di implementazione per qualsiasi classe di controllo che usa il `DECLARE_OLECREATE_EX` macro o `BEGIN_OLEFACTORY` e `END_OLEFACTORY` macro. Il nome esterno è l'identificatore del controllo OLE che viene esposta ad altre applicazioni. Contenitori di usare questo nome per richiedere un oggetto di questa classe del controllo.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxctl. h  
  
##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY  
 Inizia la dichiarazione di una factory di classe nel file di intestazione della classe del controllo.  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>Parametri  
 *CLASS_NAME*  
 Specifica il nome della classe del controllo cui factory di classe, si tratta di.  
  
### <a name="remarks"></a>Note  
 Le dichiarazioni di funzioni di gestione delle licenze factory di classe devono iniziare immediatamente dopo `BEGIN_OLEFACTORY`.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxctl. h  
  
##  <a name="end_olefactory"></a>END_OLEFACTORY  
 Termina la dichiarazione della factory di classe del controllo.  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>Parametri  
 *CLASS_NAME*  
 Il nome della classe del controllo cui factory di classe, si tratta di.  
  
### <a name="requirements"></a>Requisiti  
  **Intestazione** afxctl. h  
  
##  <a name="afxverifylicfile"></a>AfxVerifyLicFile  
 Chiamare questa funzione per verificare che il file di licenza denominato dal `pszLicFileName` è valido per il controllo OLE.  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>Parametri  
 `hInstance`  
 L'handle dell'istanza della DLL associata al controllo con licenza.  
  
 `pszLicFileName`  
 Punta a una stringa di caratteri con terminazione null contenente il nome del file di licenza.  
  
 `pszLicFileContents`  
 Punta a una sequenza di byte che deve corrispondere la sequenza trovata all'inizio del file di licenza.  
  
 `cch`  
 Numero di caratteri in `pszLicFileContents`.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se il file di licenza esista e che inizia con la sequenza di caratteri in `pszLicFileContents`; in caso contrario, 0.  
  
### <a name="remarks"></a>Note  
 Se `cch` è -1, questa funzione utilizza:  
  
 [!code-cpp[NVC_MFC_Utilities #36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>Requisiti  
  **Intestazione** afxctl. h  

## <a name="see-also"></a>Vedere anche  
 [Macro e funzioni globali](../../mfc/reference/mfc-macros-and-globals.md)
