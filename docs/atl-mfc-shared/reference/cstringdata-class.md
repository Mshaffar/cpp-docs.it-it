---
title: Classe CStringData | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
dev_langs:
- C++
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b7dfebebbec7acc774fa2e63ab9fafed788f679a
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cstringdata-class"></a>Classe CStringData
Questa classe rappresenta i dati di un oggetto stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```
struct CStringData
```  
  
## <a name="members"></a>Membri  
  
### <a name="methods"></a>Metodi  
  
|||  
|-|-|  
|[AddRef](#addref)|Incrementa il conteggio dei riferimenti dell'oggetto dati stringa.|  
|[data](#data)|Recupera i dati di carattere di un oggetto stringa.|  
|[IsLocked](#islocked)|Determina se il buffer dell'oggetto stringa associato è bloccato.|  
|[IsShared](#isshared)|Determina se il buffer dell'oggetto stringa associata viene attualmente condivisa.|  
|[Blocco](#lock)|Blocca il buffer dell'oggetto stringa associato.|  
|[Rilascio](#release)|Rilascia l'oggetto stringa specificato.|  
|[Sbloccare](#unlock)|Sblocca il buffer dell'oggetto stringa associato.|  
  
### <a name="data-members"></a>Membri di dati  
  
|||  
|-|-|  
|[nAllocLength](#nalloclength)|Lunghezza dei dati allocati `XCHAR`s (escluso a terminazione null)|  
|[nDataLength](#ndatalength)|Lunghezza dei dati attualmente in uso in `XCHAR`s (escluso a terminazione null)|  
|[nRefs](#nrefs)|Il conteggio dei riferimenti corrente dell'oggetto.|  
|[pStringMgr](#pstringmgr)|Puntatore al gestore di stringa dell'oggetto stringa.|  
  
## <a name="remarks"></a>Note  
 Questa classe deve essere utilizzata solo dagli sviluppatori che implementano i gestori di stringa personalizzata. Per ulteriori informazioni sui gestori di stringa personalizzata, vedere [gestione della memoria e CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)  
  
 Questa classe incapsula i vari tipi di informazioni e dati associati, ad esempio, un oggetto stringa superiore [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), o [CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md) oggetti. Ogni oggetto stringa superiore contiene un puntatore a essa associati `CStringData` oggetto, consentendo a più oggetti stringa in modo che punti allo stesso oggetto di dati stringa. Questa relazione è rappresentata dal conteggio dei riferimenti ( `nRefs`) di `CStringData` oggetto.  
  
> [!NOTE]
>  In alcuni casi, un tipo stringa (ad esempio **CFixedString**) non condividono un oggetto dati di stringa con più di un oggetto stringa superiore. Per ulteriori informazioni, vedere [gestione della memoria e CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 Questi dati sono composta da:  
  
-   Il gestore della memoria (di tipo [IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)) della stringa.  
  
-   La lunghezza corrente ( [nDataLength](#ndatalength)) della stringa.  
  
-   La lunghezza allocata ( [nAllocLength](#nalloclength)) della stringa. Per motivi di prestazioni, questa può essere diversa dalla lunghezza stringa corrente  
  
-   Il conteggio dei riferimenti corrente ( [nRefs](#nrefs)) di `CStringData` oggetto. Questo valore viene utilizzato per determinare il numero di oggetti stringa condividono lo stesso `CStringData` oggetto.  
  
-   Buffer di caratteri effettivi ( [dati](#data)) della stringa.  
  
    > [!NOTE]
    >  Il buffer di caratteri effettivi dell'oggetto string è allocato dal gestore di stringa e viene aggiunto il `CStringData` oggetto.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** atlsimpstr.h  
  
##  <a name="addref"></a>CStringData::AddRef  
 Incrementa il conteggio dei riferimenti dell'oggetto stringa.  
  
```
void AddRef() throw();
```  
  
### <a name="remarks"></a>Note  
 Incrementa il conteggio dei riferimenti dell'oggetto stringa.  
  
> [!NOTE]
>  Non chiamare questo metodo in una stringa con un conteggio dei riferimenti negativo, poiché un numero negativo indica che il buffer di stringa viene bloccato.  
  
##  <a name="data"></a>CStringData::data  
 Restituisce un puntatore al buffer di caratteri di un oggetto stringa.  
  
```
void* data() throw();
```  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore al buffer di caratteri dell'oggetto stringa.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione per restituire il buffer di caratteri corrente dell'oggetto stringa associato.  
  
> [!NOTE]
>  Il buffer non è allocato dal `CStringData` oggetto ma dal gestore di stringa quando necessario. Durante l'allocazione, il buffer viene aggiunto all'oggetto dati stringa.  
  
##  <a name="islocked"></a>CStringData::IsLocked  
 Determina se il buffer di caratteri è bloccato.  
  
```
bool IsLocked() const throw();
```  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce **true** se il buffer è bloccata; in caso contrario **false**.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione per determinare se il buffer di caratteri di un oggetto string è attualmente bloccato.  
  
##  <a name="isshared"></a>CStringData::IsShared  
 Determina se il buffer di caratteri è condiviso.  
  
```
bool IsShared() const throw();
```  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce **true** se il buffer è condiviso; in caso contrario **false**.  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione per determinare se il buffer di caratteri di un oggetto dati di stringa è attualmente condivisa tra più oggetti stringa.  
  
##  <a name="lock"></a>CStringData::Lock  
 Blocca il buffer di caratteri dell'oggetto stringa associato.  
  
```
void Lock() throw();
```  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione per bloccare il buffer di caratteri dell'oggetto dati stringa. Blocco e sblocco viene utilizzato quando è necessario l'accesso diretto al buffer di caratteri dallo sviluppatore. Un buon esempio di blocco viene dimostrato la [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) e [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metodi di `CSimpleStringT`.  
  
> [!NOTE]
>  È possibile bloccare un buffer di caratteri solo se il buffer non è condiviso da più oggetti stringa.  
  
##  <a name="nalloclength"></a>CStringData::nAllocLength  
 Lunghezza del buffer di caratteri allocato.  
  
```
int nAllocLength;
```  
  
### <a name="remarks"></a>Note  
 Archivia la lunghezza del buffer di dati allocati in `XCHAR`s (escluso a terminazione null).  
  
##  <a name="ndatalength"></a>CStringData::nDataLength  
 Lunghezza corrente dell'oggetto stringa.  
  
```
int nDataLength;
```  
  
### <a name="remarks"></a>Note  
 Archivia la lunghezza dei dati attualmente in uso in `XCHAR`s (escluso a terminazione null).  
  
##  <a name="nrefs"></a>CStringData::nRefs  
 Conteggio dei riferimenti dell'oggetto dati stringa.  
  
```
long nRefs;
```  
  
### <a name="remarks"></a>Note  
 Archivia il conteggio dei riferimenti dell'oggetto dati stringa. Questo contatore indica il numero di oggetti stringa superiore che sono associati all'oggetto dati di stringa. Un valore negativo indica che l'oggetto dati di stringa è attualmente bloccato.  
  
##  <a name="pstringmgr"></a>CStringData::pStringMgr  
 Il gestore della memoria dell'oggetto stringa associato.  
  
```
IAtlStringMgr* pStringMgr;
```  
  
### <a name="remarks"></a>Note  
 Archivia il gestore della memoria per l'oggetto stringa associato. Per ulteriori informazioni su stringhe e i gestori di memoria, vedere [gestione della memoria e CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
##  <a name="release"></a>CStringData::Release  
 Decrementa il conteggio dei riferimenti dell'oggetto dati stringa.  
  
```
void Release() throw();
```  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione per diminuire il conteggio dei riferimenti, liberando il `CStringData` struttura se il conteggio dei riferimenti arriva a zero. Ciò avviene in genere quando viene eliminato un oggetto stringa e pertanto non è più necessario fare riferimento all'oggetto dati di stringa.  
  
 Ad esempio, chiamare il codice seguente `CStringData::Release` per l'oggetto dati di stringa associato `str1`:  
  
 [!code-cpp[&#104; NVC_ATLMFC_Utilities](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]  
  
##  <a name="unlock"></a>CStringData::Unlock  
 Sblocca il buffer di caratteri dell'oggetto stringa associato.  
  
```
void Unlock() throw();
```  
  
### <a name="remarks"></a>Note  
 Chiamare questa funzione per sbloccare il buffer di caratteri dell'oggetto dati stringa. Dopo aver sbloccato un buffer, è condivisibile e possono essere conteggio dei riferimenti.  
  
> [!NOTE]
>  Ogni chiamata a `Lock` deve corrispondere a una chiamata corrispondente al `Unlock`.  
  
 Blocco e sblocco viene utilizzato quando lo sviluppatore deve assicurarsi che i dati della stringa non sia condivisa. Un buon esempio di blocco viene dimostrato la [LockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) e [UnlockBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) metodi di `CSimpleStringT`.  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi condivise ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


