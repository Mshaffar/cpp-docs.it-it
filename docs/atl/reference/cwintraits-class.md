---
title: Classe CWinTraits | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinTraits
- ATLWIN/ATL::CWinTraits
- ATLWIN/ATL::CWinTraits::GetWndExStyle
- ATLWIN/ATL::CWinTraits::GetWndStyle
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWinTraits class
- window styles, default values for ATL
- CWinTraits class
- CFrameWinTraits class
- CControlWinTraits class
ms.assetid: f78f486e-6d9c-42c6-8e86-371e05aa7e59
caps.latest.revision: 19
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: abd62b916f976721bf85fc4bb2a94ffaf5b217ea
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cwintraits-class"></a>Classe CWinTraits
Questa classe fornisce un metodo per la standardizzazione stili utilizzati quando si crea un oggetto finestra.  
  
> [!IMPORTANT]
>  Questa classe e i relativi membri non possono essere utilizzati nelle applicazioni eseguite in Windows Runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <DWORD t_dwStyle = 0, DWORD t_dwExStyle = 0>  class CWinTraits
```  
  
#### <a name="parameters"></a>Parametri  
 `t_dwStyle`  
 Stili di finestra standard predefiniti.  
  
 `t_dwExStyle`  
 Stili finestra estesi per impostazione predefinita.  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CWinTraits::GetWndExStyle](#getwndexstyle)|(Statico) Recupera gli stili estesi per il `CWinTraits` oggetto.|  
|[CWinTraits::GetWndStyle](#getwndstyle)|(Statico) Recupera gli stili standard per il `CWinTraits` oggetto.|  
  
## <a name="remarks"></a>Note  
 Questo [tratti finestra](../../atl/understanding-window-traits.md) classe fornisce un metodo semplice per la standardizzazione stili utilizzati per la creazione di un oggetto finestra ATL. Utilizzare una specializzazione di questa classe come un parametro di modello [CWindowImpl](../../atl/reference/cwindowimpl-class.md) o un'altra delle classi di finestra ATL per specificare gli stili estesi e standard predefinito utilizzati per le istanze di tale classe di finestra.  
  
 Utilizzare questo modello quando si desidera fornire stili finestra che verranno utilizzati solo quando gli altri stili non vengono specificati nella chiamata a predefiniti [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create).  
  
 ATL fornisce tre predefinite specializzazioni del modello per le combinazioni di stili di finestra comunemente utilizzate:  
  
 `CControlWinTraits`  
 Progettato per una finestra di controllo standard. Vengono utilizzati gli stili standard seguenti: **WS_CHILD**, **WS_VISIBLE**, **WS_CLIPCHILDREN**, e **WS_CLIPSIBLINGS**. Sono non disponibili stili estesi.  
  
 `CFrameWinTraits`  
 Progettato per una finestra cornice standard. Gli stili standard utilizzati includono: **WS_OVERLAPPEDWINDOW**, **WS_CLIPCHILDREN**, e **WS_CLIPSIBLINGS**. Gli stili estesi utilizzati includono: **WS_EX_APPWINDOW** e **WS_EX_WINDOWEDGE**.  
  
 `CMDIChildWinTraits`  
 Progettato per una finestra figlio MDI standard. Gli stili standard utilizzati includono: **WS_OVERLAPPEDWINDOW**, **WS_CHILD**, **WS_VISIBLE**, **WS_CLIPCHILDREN**, e **WS_CLIPSIBLINGS**. Gli stili estesi utilizzati includono: **WS_EX_MDICHILD**.  
  
 Se si desidera assicurarsi che siano impostati alcuni stili per tutte le istanze di classe della finestra mentre altri devono essere impostate in una base per ogni istanza, utilizzare [CWinTraitsOR](../../atl/reference/cwintraitsor-class.md) invece.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** atlwin. h  
  
##  <a name="getwndstyle"></a>CWinTraits::GetWndStyle  
 Chiamare questa funzione per recuperare gli stili di standard di `CWinTraits` oggetto.  
  
```
static DWORD GetWndStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametri  
 `dwStyle`  
 Stili utilizzati per la creazione di una finestra standard. Se `dwStyle` è 0, i valori dello stile di modello ( `t_dwStyle`) vengono restituiti. Se `dwStyle` è diverso da zero, `dwStyle` viene restituito.  
  
### <a name="return-value"></a>Valore restituito  
 Gli stili di finestra standard dell'oggetto.  
  
##  <a name="getwndexstyle"></a>CWinTraits::GetWndExStyle  
 Chiamare questa funzione per recuperare gli stili estesi di `CWinTraits` oggetto.  
  
```
static DWORD GetWndExStyle(DWORD dwExStyle);
```  
  
### <a name="parameters"></a>Parametri  
 `dwExStyle`  
 Stili estesi utilizzati per la creazione di una finestra. Se `dwExStyle` è 0, i valori dello stile di modello ( `t_dwExStyle`) vengono restituiti. Se `dwExStyle` è diverso da zero, `dwExStyle` viene restituito.  
  
### <a name="return-value"></a>Valore restituito  
 Stili finestra estesi dell'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di classe](http://msdn.microsoft.com/en-us/dbe6a147-3f01-4aea-a3fb-fe6ebadc31f8)   
 [Cenni preliminari sulla classe](../../atl/atl-class-overview.md)   
 [Informazioni sulle caratteristiche di finestra](../../atl/understanding-window-traits.md)
