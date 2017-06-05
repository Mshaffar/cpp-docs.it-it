---
title: Classe CMFCCmdUsageCount | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
dev_langs:
- C++
helpviewer_keywords:
- CMFCCmdUsageCount class
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 20
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
ms.openlocfilehash: b264448af4041139018b181e2255988555267b89
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccmdusagecount-class"></a>Classe CMFCCmdUsageCount
Registra il conteggio di utilizzo di messaggi di Windows, ad esempio quando l'utente seleziona un elemento da un menu.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|||  
|-|-|  
|Nome|Descrizione|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Costruttore predefinito.|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Distruttore.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|||  
|-|-|  
|Nome|Descrizione|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Viene incrementato di uno il contatore che viene associato al comando specificato.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|Recupera il conteggio di utilizzo che viene associato all'ID di comando specificato.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Determina se la quantità minima di rilevamento dei dati è raccolti da questo oggetto.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Determina se il comando specificato è frequente.|  
|[CMFCCmdUsageCount::Reset](#reset)|Cancella il conteggio di utilizzo di tutti i comandi.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Legge l'oggetto da un archivio o scrive in un archivio. (Esegue l'override di [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Imposta i valori di condivisi `CMFCCmdUsageCount` i membri dati della classe.|  
  
### <a name="data-members"></a>Membri di dati  
  
|||  
|-|-|  
|Nome|Descrizione|  
|`m_CmdUsage`|Oggetto `CMap` che esegue il mapping di comandi per i conteggi dell'utilizzo.|  
|`m_nMinUsagePercentage`|La percentuale di utilizzo minimo per un comando per essere utilizzati.|  
|`m_nStartCount`|Il contatore di avvio che viene utilizzato per determinare se la quantità minima di rilevamento dei dati è raccolti da questo oggetto.|  
|`m_nTotalUsage`|Il numero di comandi tutte le revisioni.|  
  
### <a name="remarks"></a>Note  
 La `CMFCCmdUsageCount` classe esegue il mapping di ogni identificatore di messaggio Windows numerico in un contatore intero senza segno a 32 bit. `CMFCToolBar`utilizza questa classe per visualizzare gli elementi utilizzati di frequente della barra degli strumenti. Per ulteriori informazioni su `CMFCToolBar`, vedere [CMFCToolBar classe](../../mfc/reference/cmfctoolbar-class.md).  
  
 È possibile rendere persistente `CMFCCmdUsageCount` classe di dati tra le esecuzioni del programma. Utilizzare il [CMFCCmdUsageCount::Serialize](#serialize) metodo per serializzare dati membro di classe e il [CMFCCmdUsageCount::SetOptions](#setoptions) per impostare i dati dei membri condivisi.  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 Viene incrementato di uno il contatore che viene associato al comando specificato.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `uiCmd`|Specifica il contatore di comando da incrementare.|  
  
### <a name="remarks"></a>Note  
 Questo metodo aggiunge una nuova voce per la struttura della mappa dei conteggi di comando, `m_CmdUsage`, se la voce non esiste già.  
  
 Questo metodo non esegue alcuna operazione nei casi seguenti:  
  
-   Il framework della barra degli strumenti è in modalità di personalizzazione (il [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) metodo restituisce un valore diverso da zero).  
  
-   Il comando fa riferimento a un separatore di menu o di sottomenu ( `uiCmd` uguale a 0 o -1).  
  
- `uiCmd`fa riferimento a un comando standard (globale `IsStandardCommand` funzione restituisce un valore diverso da zero).  
  
##  <a name="getcount"></a>CMFCCmdUsageCount::GetCount  
 Recupera il conteggio di utilizzo che viene associato all'ID di comando specificato.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `uiCmd`|L'ID del contatore di comando da recuperare.|  
  
### <a name="return-value"></a>Valore restituito  
 Il conteggio di utilizzo che viene associato all'ID di comando specificato.  
  
##  <a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 Determina se questo oggetto ha ricevuto la quantità minima di dati di rilevamento.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se l'oggetto ha ricevuto la quantità minima di rilevamento di dati. in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Questo metodo restituisce un valore diverso da zero se il conteggio totale `m_nTotalUsage`, di tutte le revisioni comandi è uguale o maggiore rispetto al numero iniziale, `m_nStartCount`. Per impostazione predefinita, il framework imposta il numero iniziale di 0. È possibile eseguire l'override di questo valore utilizzando il [CMFCCmdUsageCount::SetOptions](#setoptions) metodo.  
  
 Questo metodo viene utilizzato da [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) per determinare se mostrare tutti i comandi di menu disponibili.  
  
##  <a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Determina se il comando specificato è frequente.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `uiCmd`|Specifica il comando da controllare.|  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se il comando viene spesso usato; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Questo metodo restituisce 0 se la sintassi del comando totale, `m_nTotalUsage`, è 0. In caso contrario, questo metodo viene restituito diverso da zero se la percentuale di cui viene utilizzato il comando specificato è maggiore della percentuale minima `m_nMinUsagePercentage`. Per impostazione predefinita, il framework imposta la percentuale minima di 5. È possibile eseguire l'override di questo valore utilizzando il [CMFCCmdUsageCount::SetOptions](#setoptions) metodo. Se la percentuale minima è 0, questo metodo restituisce zero se il numero di comandi specificato è maggiore di 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) utilizza questo metodo per determinare se un comando viene utilizzato raramente.  
  
##  <a name="reset"></a>CMFCCmdUsageCount::Reset  
 Cancella il conteggio di utilizzo di tutti i comandi.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Note  
 Chiamare questo metodo per cancellare tutte le voci dalla struttura di mappa dei conteggi di comando, `m_CmdUsage`e per reimpostare la sintassi del comando totale, `m_nTotalUsage`, il contatore su 0.  
  
##  <a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 Legge l'oggetto da un archivio o scrive in un archivio.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `ar`|Oggetto `CArchive` oggetto da serializzare da o a.|  
  
### <a name="remarks"></a>Note  
 Questo metodo serializza la struttura della mappa dei conteggi di comando, `m_CmdUsage`e la sintassi del comando totale, `m_nTotalUsage`, il contatore da o verso l'archivio specificato.  
  
 Per esempi di serializzazione, vedere [serializzazione: serializzazione di un oggetto](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
 Imposta i valori di condivisi `CMFCCmdUsageCount` i membri dati della classe.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>Parametri  
  
|||  
|-|-|  
|Parametro|Descrizione|  
|[in] `nStartCount`|Nuovo numero iniziale di tutte le revisioni comandi.|  
|[in] `nMinUsagePercentage`|La nuova percentuale di utilizzo minimo.|  
  
### <a name="return-value"></a>Valore restituito  
 `TRUE`Se il metodo ha esito positivo, `FALSE` se il `nMinUsagePercentage` parametro è maggiore o uguale a 100.  
  
### <a name="remarks"></a>Note  
 Questo metodo imposta condivisa `CMFCCmdUsageCount` i membri dati della classe `m_nStartCount` e `m_nMinUsagePercentage` a `nStartCount` e `nMinUsagePercentage`, rispettivamente. `m_nStartCount`viene utilizzato il [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) metodo per determinare se la quantità minima di rilevamento dei dati è raccolti da questo oggetto. `m_nMinUsagePercentage`viene utilizzato il [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) metodo per determinare se un determinato comando è frequente.  
  
 Nelle build di Debug questo metodo genera un errore di asserzione se il `nMinUsagePercentage` parametro è maggiore o uguale a 100.  
  
## <a name="see-also"></a>Vedere anche  
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classi](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
