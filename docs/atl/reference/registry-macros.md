---
title: Le macro del Registro di sistema | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
caps.latest.revision: 16
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
ms.openlocfilehash: 3a3abf5ad29b50c7f6708f02fd7c5aa193b3591c
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="registry-macros"></a>Macro del Registro di sistema
Queste macro definiscono strutture di libreria e del Registro di sistema di tipo utile.  
  
|||  
|-|-|  
|[ATL_STATIC_REGISTRY](#_atl_static_registry)|Indica che si desidera che il codice di registrazione per l'oggetto sia l'oggetto per evitare una dipendenza su ATL. DLL.|  
|[DECLARE_LIBID](#declare_libid)|Fornisce un modo per ATL ottenere il *libid* della libreria dei tipi.|  
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Evita la registrazione ATL predefinito.|  
|[DECLARE_REGISTRY](#declare_registry)|Entra o rimuove una voce dell'oggetto principale nel Registro di sistema.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Specifica le informazioni necessarie per registrare automaticamente il *appid*.|  
|[MACRO DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Trova la risorsa specificata e viene eseguito lo script del Registro di sistema.|  
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Trova la risorsa identificata da un numero di ID e viene eseguito lo script del Registro di sistema.|  

## <a name="requirements"></a>Requisiti  
 **Intestazione:** atlcom. h  
  
    
##  <a name="_atl_static_registry"></a>ATL_STATIC_REGISTRY  
 Un simbolo che indica che si desidera che il codice di registrazione per l'oggetto sia l'oggetto per evitare una dipendenza su ATL. DLL.  
  
```
#define _ATL_STATIC_REGISTRY
```  
  
### <a name="remarks"></a>Note  
 Quando si definisce **ATL_STATIC_REGISTRY**, è consigliabile utilizzare il codice seguente:  
  
 [!code-cpp[NVC_ATL_EventHandlingSample n.&5;](../../atl/codesnippet/cpp/registry-macros_1.cpp)]  
  
##  <a name="declare_libid"></a>DECLARE_LIBID  
 Fornisce un modo per ATL ottenere il *libid* della libreria dei tipi.  
  
```
DECLARE_LIBID( libid )
```  
  
### <a name="parameters"></a>Parametri  
 *LIBID*  
 Il GUID della libreria dei tipi.  
  
### <a name="remarks"></a>Note  
 Utilizzare `DECLARE_LIBID` in un `CAtlModuleT`-classe derivata.  
  
### <a name="example"></a>Esempio  
 Attributi non generato dalla procedura guidata ATL (progetti) avrà un esempio dell'utilizzo di questa macro.  
  
##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY  
 Utilizzare `DECLARE_NO_REGISTRY` se si desidera evitare qualsiasi registrazione ATL predefinito per la classe in cui viene visualizzata questa macro.  
  
```
DECLARE_NO_REGISTRY()
```  
  
##  <a name="declare_registry"></a>DECLARE_REGISTRY  
 Immette la registrazione della classe standard nel Registro di sistema o lo rimuove dal Registro di sistema.  
  
```
DECLARE_REGISTRY(
    class, 
    pid, 
    vpid, 
    nid, 
    flags )
```  
  
### <a name="parameters"></a>Parametri  
 `class`  
 [in] Incluso per compatibilità con le versioni precedenti.  
  
 `pid`  
 [in] Un `LPCTSTR` che è un ID di programma specifici della versione.  
  
 *vpid*  
 [in] Un `LPCTSTR` che è un ID di programma indipendente dalla versione.  
  
 *nID*  
 [in] Oggetto **UINT** che è un indice della stringa di risorsa nel Registro di sistema da utilizzare come la descrizione del programma.  
  
 `flags`  
 [in] Oggetto `DWORD` contenente il programma di modello di threading nel Registro di sistema. Deve essere uno dei seguenti valori: **THREADFLAGS_APARTMENT**, **THREADFLAGS_BOTH**, o **AUTPRXFLAG**.  
  
### <a name="remarks"></a>Note  
 La registrazione standard è costituito il CLSID, ID di programma, ID di programma indipendente dalla versione, la stringa di descrizione e modello di Threading.  
  
 Quando si crea un oggetto o controllo utilizzando la creazione guidata classe aggiungere ATL, la procedura guidata implementa il supporto del Registro di sistema basato su script automaticamente e aggiunge il [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) macro nei file. Se non si desidera supporto basato su script del Registro di sistema, è necessario sostituire questa macro con `DECLARE_REGISTRY`. `DECLARE_REGISTRY`Consente di inserire solo le chiavi di base cinque descritte in precedenza nel Registro di sistema. È necessario scrivere manualmente codice per inserire altre chiavi del Registro di sistema.  
  
##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID  
 Specifica le informazioni necessarie per registrare automaticamente il *appid*.  
  
```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid, 
    appid )
```  
  
### <a name="parameters"></a>Parametri  
 *RESID*  
 L'id di risorsa del file con estensione RGS che contiene informazioni sui *appid*.  
  
 *AppID*  
 Un valore GUID.  
  
### <a name="remarks"></a>Note  
 Utilizzare `DECLARE_REGISTRY_APPID_RESOURCEID` in un `CAtlModuleT`-classe derivata.  
  
### <a name="example"></a>Esempio  
 Le classi aggiunte a ATL (progetti) con la creazione guidata aggiunta classe dispongono di un esempio dell'utilizzo di questa macro.  
  
##  <a name="declare_registry_resource"></a>MACRO DECLARE_REGISTRY_RESOURCE  
 Ottiene la risorsa specificata che contiene il file del Registro di sistema e viene eseguito lo script per immettere gli oggetti nel Registro di sistema o rimuoverli dal Registro di sistema.  
  
```
DECLARE_REGISTRY_RESOURCE( x )
```  
  
### <a name="parameters"></a>Parametri  
 *x*  
 [in] Identificatore della risorsa di stringa.  
  
### <a name="remarks"></a>Note  
 Quando si crea un oggetto o controllo utilizzando la creazione guidata progetto ATL, verranno automaticamente implementano il supporto del Registro di sistema basato su script e aggiungere il [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) (macro), che è simile a `DECLARE_REGISTRY_RESOURCE`, ai file.  
  
 È possibile collegare in modo statico con il componente del Registro di sistema ATL (Registrar) per l'accesso al registro ottimizzato. Per collegare in modo statico il codice di registrazione, aggiungere la riga seguente al file stdafx h:  
  
 [!code-cpp[NVC_ATL_COM &#56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Se si desidera ATL per sostituire i valori di sostituzione in fase di esecuzione, non si specifica il `DECLARE_REGISTRY_RESOURCE` o `DECLARE_REGISTRY_RESOURCEID` (macro). In alternativa, creare una matrice di **_ATL_REGMAP_ENTRIES** strutture, in cui ogni voce contiene un segnaposto di variabili abbinato con un valore di sostituire il segnaposto in fase di esecuzione. Quindi chiamare [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), passando la matrice. Aggiunge tutti i valori di sostituzione nel **_ATL_REGMAP_ENTRIES** strutture alla mappa di sostituzione del Registrar.  

  
 Per ulteriori informazioni sui parametri sostituibili e script, vedere l'articolo [il componente del Registro di sistema ATL (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID  
 Uguale a [macro DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) ad eccezione del fatto che utilizza una procedura guidata genera **UINT** per identificare la risorsa, anziché un nome di stringa.  
  
```
DECLARE_REGISTRY_RESOURCEID( x )
```  
  
### <a name="parameters"></a>Parametri  
 *x*  
 [in] Identificatore generato dalla procedura guidata della risorsa.  
  
### <a name="remarks"></a>Note  
 Quando si crea un oggetto o controllo utilizzando la creazione guidata progetto ATL, verranno automaticamente implementano il supporto del Registro di sistema basato su script e aggiungere il `DECLARE_REGISTRY_RESOURCEID` macro nei file.  
  
 È possibile collegare in modo statico con il componente del Registro di sistema ATL (Registrar) per l'accesso al registro ottimizzato. Per collegare in modo statico il codice di registrazione, aggiungere la riga seguente al file stdafx h:  
  
 [!code-cpp[NVC_ATL_COM &#56;](../../atl/codesnippet/cpp/registry-macros_2.h)]  
  
 Se si desidera ATL per sostituire i valori di sostituzione in fase di esecuzione, non si specifica il `DECLARE_REGISTRY_RESOURCE` o `DECLARE_REGISTRY_RESOURCEID` (macro). In alternativa, creare una matrice di **_ATL_REGMAP_ENTRIES** strutture, in cui ogni voce contiene un segnaposto di variabili abbinato con un valore di sostituire il segnaposto in fase di esecuzione. Quindi chiamare [CAtlModule:: UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) o [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources), passando la matrice. Aggiunge tutti i valori di sostituzione nel **_ATL_REGMAP_ENTRIES** strutture alla mappa di sostituzione del Registrar.  

  
 Per ulteriori informazioni sui parametri sostituibili e script, vedere l'articolo [il componente del Registro di sistema ATL (Registrar)](../../atl/atl-registry-component-registrar.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Macro](../../atl/reference/atl-macros.md)
