---
title: Classe CMapStringToOb | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapStringToOb
- AFXCOLL/CMapStringToOb
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs:
- C++
helpviewer_keywords:
- collection classes, string mapping
- CMapStringToOb class
- strings [C++], class for mapping
ms.assetid: 09653980-b885-4f3a-8594-0aeb7f94c601
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
ms.openlocfilehash: 2bfd277ebc1f00784d8e3d9686623777cb7fb5a5
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cmapstringtoob-class"></a>Classe CMapStringToOb
Classe di raccolte dizionario che esegue il mapping di oggetti `CString` univoci ai puntatori `CObject` .  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CMapStringToOb : public CObject  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](#cmapstringtoob)|Costruttore.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](#getcount)|Restituisce il numero di elementi nella mappa.|  
|[CMapStringToOb::GetHashTableSize](#gethashtablesize)|Determina il numero corrente di elementi nella tabella hash.|  
|[CMapStringToOb::GetNextAssoc](#getnextassoc)|Ottiene l'elemento successivo per l'iterazione.|  
|[CMapStringToOb::GetSize](#getsize)|Restituisce il numero di elementi nella mappa.|  
|[CMapStringToOb::GetStartPosition](#getstartposition)|Restituisce la posizione del primo elemento.|  
|[CMapStringToOb::HashKey](#hashkey)|Calcola il valore hash di una chiave specificata.|  
|[CMapStringToOb::InitHashTable](#inithashtable)|Inizializza la tabella hash.|  
|[CMapStringToOb::IsEmpty](#isempty)|Verifica se la condizione mappa vuota (nessun elemento).|  
|[CMapStringToOb::Lookup](#lookup)|Cerca un puntatore void in base alla chiave di un puntatore void. Il valore del puntatore, non l'entità cui fa riferimento, viene utilizzato per il confronto delle chiavi.|  
|[CMapStringToOb::LookupKey](#lookupkey)|Restituisce un riferimento alla chiave associata al valore di chiave specificato.|  
|[CMapStringToOb::RemoveAll](#removeall)|Rimuove tutti gli elementi da questa mappa.|  
|[CMapStringToOb::RemoveKey](#removekey)|Rimuove un elemento specificato da una chiave.|  
|[CMapStringToOb::SetAt](#setat)|Inserisce un elemento nella mappa. sostituisce un elemento esistente se viene trovata una chiave corrispondente.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[[CMapStringToOb::operator]](#operator_at)|Inserisce un elemento nella mappa, la sostituzione di operatore per `SetAt`.|  
  
## <a name="remarks"></a>Note  
 Dopo aver inserito un `CString` -  `CObject*` coppia (elemento) nella mappa, è possibile recuperare in modo efficiente o eliminare la coppia utilizzando una stringa o un `CString` valore come chiave. È inoltre possibile scorrere tutti gli elementi nella mappa.  
  
 Una variabile di tipo **posizione** viene utilizzato per l'accesso alternativo voce in tutte le variazioni di mappa. È possibile utilizzare un **posizione** per una voce "ricorda" e per l'iterazione attraverso la mappa. Si potrebbe pensare che l'iterazione è sequenziale in base al valore della chiave; non è. La sequenza di elementi recuperati è indeterminata.  
  
 `CMapStringToOb` incorpora la macro `IMPLEMENT_SERIAL` per supportare la serializzazione e il dump dei relativi elementi. Ogni elemento viene serializzato, a sua volta se una mappa è archiviata in un archivio, con l'inserimento di overload ( ** << **) (operatore) o con il `Serialize` funzione membro.  
  
 Se è necessario un dump di diagnostica dei singoli elementi nella mappa (il `CString` valore e il `CObject` contenuto), è necessario impostare la profondità del contesto di dump a 1 o superiore.  
  
 Quando un `CMapStringToOb` oggetto viene eliminato oppure quando gli elementi vengono rimossi, il `CString` oggetti e `CObject` i puntatori vengono rimossi. Gli oggetti a cui fa riferimento il `CObject` puntatori non vengono eliminati.  
  
 Derivazione di classi di mappa è simile alla derivazione di elenco. Vedere l'articolo [raccolte](../../mfc/collections.md) per un'illustrazione di derivazione di una classe speciale elenco.  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToOb`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxcoll. h  
  
##  <a name="cmapstringtoob"></a>CMapStringToOb::CMapStringToOb  
 Costruisce un oggetto vuoto `CString`- a - `CObject*` mappa.  
  
```  
CMapStringToOb(INT_PTR nBlockSize = 10);
```  
  
### <a name="parameters"></a>Parametri  
 `nBlockSize`  
 Specifica la granularità di allocazione della memoria per l'estensione della mappa.  
  
### <a name="remarks"></a>Note  
 Man mano che aumenta la mappa, la memoria viene allocata in unità di `nBlockSize` voci.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a **CMapStringToOb:: CMapStringToOb**.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**CMapPtrToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**CMapPtrToWord (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**CMapStringToPtr (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CMapStringToString (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CMapWordToOb (INT_PTR** `nBlockSize` **= 10);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**MapWordToPtr (INT_PTR** `nBlockSize` **= 10);**|  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCCollections&#63;](../../mfc/codesnippet/cpp/cmapstringtoob-class_1.cpp)]  
  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
##  <a name="getcount"></a>CMapStringToOb::GetCount  
 Determina il numero di elementi nella mappa.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di elementi nella mappa.  
  
### <a name="remarks"></a>Note  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::GetCount`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**() GetCount INT_PTR const.**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**() GetCount INT_PTR const.**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**() GetCount INT_PTR const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**() GetCount INT_PTR const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**() GetCount INT_PTR const.**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**() GetCount INT_PTR const.**|  
  
### <a name="example"></a>Esempio  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
 [!code-cpp[&#64; NVC_MFCCollections](../../mfc/codesnippet/cpp/cmapstringtoob-class_2.cpp)]  
  
##  <a name="gethashtablesize"></a>CMapStringToOb::GetHashTableSize  
 Determina il numero corrente di elementi nella tabella hash.  
  
```  
UINT GetHashTableSize() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce il numero di elementi nella tabella hash.  
  
### <a name="remarks"></a>Note  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::GetHashTableSize`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT () di GetHashTableSize const.**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT () di GetHashTableSize const.**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT () di GetHashTableSize const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT () di GetHashTableSize const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**UINT () di GetHashTableSize const.**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**UINT () di GetHashTableSize const.**|  
  
##  <a name="getnextassoc"></a>CMapStringToOb::GetNextAssoc  
 Recupera l'elemento della mappa in *rNextPosition*, quindi Aggiorna *rNextPosition* per fare riferimento all'elemento successivo nella mappa.  
  
```  
void GetNextAssoc(
    POSITION& rNextPosition,  
    CString& rKey,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametri  
 *rNextPosition*  
 Specifica un riferimento a un **posizione** valore restituito da una precedente **GetNextAssoc** o **GetStartPosition** chiamare.  
  
 *rKey*  
 Specifica la chiave restituita dell'elemento recuperato (stringa).  
  
 *rValue*  
 Specifica il valore restituito dell'elemento recuperato (un **CObject** puntatore). Per ulteriori informazioni su questo parametro, vedere la sezione Osservazioni.  
  
### <a name="remarks"></a>Note  
 Questa funzione è particolarmente utile per scorrere tutti gli elementi nella mappa. Si noti che la sequenza di posizione non è necessariamente uguale sequenza il valore della chiave.  
  
 Se l'elemento recuperato è l'ultimo nella mappa, quindi il nuovo valore di *rNextPosition* è impostato su **NULL**.  
  
 Per il *rValue* parametro, assicurarsi di eseguire il cast del tipo di oggetto **CObject\*&**, che è ciò che richiede al compilatore, come illustrato nell'esempio seguente:  
  
 [!code-cpp[NVC_MFCCollections&#65;](../../mfc/codesnippet/cpp/cmapstringtoob-class_3.cpp)]  
  
 Questo non vale **GetNextAssoc** per le mappe basate su modelli.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a **CMapStringToOb::GetNextAssoc**.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, void\*&** *rValue* **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, void\*&** *rKey* **, WORD&** *rValue* **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void GetNextAssoc (posizione /** *rNextPosition* **, CString /** *rKey* **, void\* & ** *rValue* **) const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void GetNextAssoc (posizione /** *rNextPosition* **, CString /** *rKey* **, CString /** *rValue* **) const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void GetNextAssoc (posizione /** *rNextPosition* **, WORD /** *rKey* **, CObject\* & ** *rValue* **) const.**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void GetNextAssoc( POSITION&** *rNextPosition* **, WORD&** *rKey* **, void\*&** *rValue* **) const;**|  
  
### <a name="example"></a>Esempio  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
 [!code-cpp[NVC_MFCCollections n.&66;](../../mfc/codesnippet/cpp/cmapstringtoob-class_4.cpp)]  
  
 I risultati di questo programma sono come segue:  
  
 `Lisa : a CAge at $4724 11`  
  
 `Marge : a CAge at $47A8 35`  
  
 `Homer : a CAge at $4766 36`  
  
 `Bart : a CAge at $45D4 13`  
  
##  <a name="getsize"></a>CMapStringToOb::GetSize  
 Restituisce il numero di elementi della mappa.  
  
```  
INT_PTR GetSize() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di elementi nella mappa.  
  
### <a name="remarks"></a>Note  
 Chiamare questo metodo per recuperare il numero di elementi nella mappa.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::GetSize`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**() GetSize INT_PTR const.**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**() GetSize INT_PTR const.**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**() GetSize INT_PTR const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**() GetSize INT_PTR const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**() GetSize INT_PTR const.**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**() GetSize INT_PTR const.**|  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_MFCCollections&#67;](../../mfc/codesnippet/cpp/cmapstringtoob-class_5.cpp)]  
  
##  <a name="getstartposition"></a>CMapStringToOb::GetStartPosition  
 Inizia un'iterazione mappa restituendo un **posizione** che può essere passato a un `GetNextAssoc` chiamare.  
  
```  
POSITION GetStartPosition() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto **posizione** valore che indica una posizione iniziale per l'iterazione della mappa; o **NULL** se la mappa è vuota.  
  
### <a name="remarks"></a>Note  
 La sequenza di iterazione non è stimabile; Pertanto, il "primo elemento nella mappa" alcun significato speciale.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::GetStartPosition`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**POSIZIONE () GetStartPosition const.**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**POSIZIONE () GetStartPosition const.**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**POSIZIONE () GetStartPosition const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**POSIZIONE () GetStartPosition const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**POSIZIONE () GetStartPosition const.**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**POSIZIONE () GetStartPosition const.**|  
  
### <a name="example"></a>Esempio  
 Vedere l'esempio per [CMapStringToOb::GetNextAssoc](#getnextassoc).  
  
##  <a name="hashkey"></a>CMapStringToOb::HashKey  
 Calcola il valore hash di una chiave specificata.  
  
```  
UINT HashKey(LPCTSTR key) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `key`  
 Chiave il cui valore hash viene calcolato.  
  
### <a name="return-value"></a>Valore restituito  
 Il valore della chiave hash  
  
### <a name="remarks"></a>Note  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::HashKey`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**UINT HashKey (void\* ** `key` **) const.**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**UINT HashKey (void\* ** `key` **) const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**UINT HashKey (LPCTSTR** `key` **) const.**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**UINT HashKey (LPCTSTR** `key` **) const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**HashKey UINT (parola** `key` **) const.**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**HashKey UINT (parola** `key` **) const.**|  
  
##  <a name="inithashtable"></a>CMapStringToOb::InitHashTable  
 Inizializza la tabella hash.  
  
```  
void InitHashTable(
    UINT hashSize,  
    BOOL bAllocNow = TRUE);
```  
  
### <a name="parameters"></a>Parametri  
 `hashSize`  
 Numero di voci nella tabella hash.  
  
 `bAllocNow`  
 Se **TRUE**, consente di allocare la tabella di hash al momento dell'inizializzazione; in caso contrario la tabella viene allocata quando necessario.  
  
### <a name="remarks"></a>Note  
 Per prestazioni ottimali, le dimensioni della tabella hash devono essere un numero primo. Per ridurre al minimo i conflitti, la dimensione deve essere approssimativamente il 20% maggiore di set di dati più grande previsto.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::InitHashTable`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void InitHashTable (UINT** `hashSize` **, BOOL** `bAllocNow` **= TRUE);**|  
  
##  <a name="isempty"></a>CMapStringToOb::IsEmpty  
 Determina se la mappa è vuota.  
  
```  
BOOL IsEmpty() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se questa mappa non contiene elementi; in caso contrario 0.  
  
### <a name="example"></a>Esempio  
 Vedere l'esempio per [RemoveAll](#removeall).  
  
### <a name="remarks"></a>Note  
 Nella tabella seguente mostra altri membri funzioni che sono simili a **CMapStringToOb:: IsEmpty**.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**IsEmpty BOOL () const.**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**IsEmpty BOOL () const.**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**IsEmpty BOOL () const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**IsEmpty BOOL () const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**IsEmpty BOOL () const.**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**IsEmpty BOOL () const.**|  
  
##  <a name="lookup"></a>CMapStringToOb::Lookup  
 Restituisce un `CObject` puntatore basato su un `CString` valore.  
  
```  
BOOL Lookup(
    LPCTSTR key,  
    CObject*& rValue) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `key`  
 Specifica la chiave di stringa che identifica l'elemento cercato.  
  
 `rValue`  
 Specifica il valore restituito dall'elemento cercato.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se l'elemento è stato trovato; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 `Lookup`utilizza un algoritmo di hash per trovare rapidamente l'elemento della mappa con una chiave che corrispondono esattamente ( `CString` valore).  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::LookUp`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL Lookup( void\*** `key` **, void\*&** `rValue` **) const;**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL Lookup( void\*** `key` **, WORD&** `rValue` **) const;**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL Lookup( LPCTSTR** `key` **, void\*&** `rValue` **) const;**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**Ricerca BOOL (LPCTSTR** `key` **, CString /** `rValue` **) const.**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL Lookup( WORD** `key` **, CObject\*&** `rValue` **) const;**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL Lookup( WORD** `key` **, void\*&** `rValue` **) const;**|  
  
### <a name="example"></a>Esempio  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
 [!code-cpp[NVC_MFCCollections&#68;](../../mfc/codesnippet/cpp/cmapstringtoob-class_6.cpp)]  
  
##  <a name="lookupkey"></a>CMapStringToOb::LookupKey  
 Restituisce un riferimento alla chiave associata al valore di chiave specificato.  
  
```  
BOOL LookupKey(
    LPCTSTR key,  
    LPCTSTR& rKey) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `key`  
 Specifica la chiave di stringa che identifica l'elemento cercato.  
  
 `rKey`  
 Riferimento per la chiave associata.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se la chiave viene trovata; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Utilizzando un riferimento a una chiave è sicuro se utilizzato dopo l'elemento associato è stato rimosso dalla mappa o dopo che la mappa è stata eliminata.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a **CMapStringToOb:: LookupKey**.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR /** `rKey` **) const.**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL LookupKey (LPCTSTR** `key` **, LPCTSTR /** `rKey` **) const.**|  
  
##  <a name="operator_at"></a>[CMapStringToOb::operator]  
 Per sostituire pratico di `SetAt` funzione membro.  
  
```  
CObject*& operator[ ](lpctstr key);
```  
  
### <a name="return-value"></a>Valore restituito  
 Un riferimento a un puntatore a un `CObject` ; dell'oggetto o **NULL** se la mappa è vuota o `key` non compreso nell'intervallo.  
  
### <a name="remarks"></a>Note  
 In questo modo può essere utilizzato solo sul lato sinistro di un'istruzione di assegnazione (un l-value). Se non esiste nessun elemento della mappa con la chiave specificata, viene creato un nuovo elemento.  
  
 Non esiste alcun "destra" (r) equivalente all'operatore perché vi è la possibilità che una chiave potrebbe non essere trovata nella mappa. Utilizzare il `Lookup` una funzione membro per il recupero di elemento.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a **CMapStringToOb::operator [**.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void\*& operator[](void\*** `key` **\);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**WORD& operator[](void\*** `key` **\);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void\*& operator[](lpctstr** `key` **\);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**CString / (operatore) [] (lpctstr** `key` ** \);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**CObject\*& operator[](word** `key` **\);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void\*& operator[](word** `key` **\);**|  
  
### <a name="example"></a>Esempio  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
 [!code-cpp[NVC_MFCCollections&#72;](../../mfc/codesnippet/cpp/cmapstringtoob-class_7.cpp)]  
  
 I risultati di questo programma sono come segue:  
  
 `Operator [] example: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $4A02 11`  
  
 `[Bart] = a CAge at $497E 13`  
  
##  <a name="removeall"></a>CMapStringToOb::RemoveAll  
 Rimuove tutti gli elementi da questa mappa ed elimina il `CString` gli oggetti della chiave.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Note  
 Il `CObject` non vengono eliminati gli oggetti a cui fa riferimento da ciascuna chiave. Il `RemoveAll` funzione può causare perdite di memoria se si garantisce che il riferimento `CObject` gli oggetti vengono eliminati.  
  
 La funzione funziona correttamente se la mappa è vuota.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::RemoveAll`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void RemoveAll ();**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void RemoveAll ();**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void RemoveAll ();**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void RemoveAll ();**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void RemoveAll ();**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void RemoveAll ();**|  
  
### <a name="example"></a>Esempio  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
 [!code-cpp[NVC_MFCCollections&#69;](../../mfc/codesnippet/cpp/cmapstringtoob-class_8.cpp)]  
  
##  <a name="removekey"></a>CMapStringToOb::RemoveKey  
 Cerca la voce della mappa corrispondente alla chiave fornita; quindi, se la chiave viene trovata, rimuove la voce.  
  
```  
BOOL RemoveKey(LPCTSTR key);
```  
  
### <a name="parameters"></a>Parametri  
 `key`  
 Specifica la stringa utilizzata per la ricerca della mappa.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se la voce è stata trovata e rimosso correttamente; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Ciò può provocare perdite di memoria se il `CObject` oggetto non viene eliminato in un' posizione.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::RemoveKey`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**BOOL RemoveKey (void\* ** `key` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**BOOL RemoveKey (void\* ** `key` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**BOOL RemoveKey (LPCTSTR** `key` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**BOOL RemoveKey (WORD** `key` **);**|  
  
### <a name="example"></a>Esempio  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
 [!code-cpp[NVC_MFCCollections&#70;](../../mfc/codesnippet/cpp/cmapstringtoob-class_9.cpp)]  
  
 I risultati di questo programma sono come segue:  
  
 `RemoveKey example: A CMapStringToOb with 3 elements`  
  
 `[Marge] = a CAge at $49A0 35`  
  
 `[Homer] = a CAge at $495E 36`  
  
 `[Bart] = a CAge at $4634 13`  
  
##  <a name="setat"></a>CMapStringToOb::SetAt  
 I due principali strumenti inserire un elemento in una mappa.  
  
```  
void SetAt(
    LPCTSTR key,  
    CObject* newValue);
```  
  
### <a name="parameters"></a>Parametri  
 `key`  
 Specifica la stringa che rappresenta la chiave del nuovo elemento.  
  
 `newValue`  
 Specifica il `CObject` puntatore che rappresenta il valore del nuovo elemento.  
  
### <a name="remarks"></a>Note  
 Innanzitutto, viene cercata la chiave. Se la chiave viene trovata, quindi verrà modificato il valore corrispondente. in caso contrario, viene creato un nuovo elemento chiave-valore.  
  
 Nella tabella seguente mostra altri membri funzioni che sono simili a `CMapStringToOb::SetAt`.  
  
|Classe|Funzione membro|  
|-----------|---------------------|  
|[CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)|**void SetAt( void\*** `key` **, void\*** `newValue` **);**|  
|[CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)|**void SetAt( void\*** `key` **, WORD** `newValue` **);**|  
|[CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)|**void SetAt( LPCTSTR** `key` **, void\*** `newValue` **);**|  
|[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)|**void SetAt( LPCTSTR** `key` **, LPCTSTR** `newValue` **);**|  
|[CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)|**void SetAt( WORD** `key` **, CObject\*** `newValue` **);**|  
|[CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)|**void SetAt( WORD** `key` **, void\*** `newValue` **);**|  
  
### <a name="example"></a>Esempio  
 Vedere [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) per un elenco della `CAge` classe utilizzata in tutti gli esempi di raccolta.  
  
 [!code-cpp[NVC_MFCCollections&#71;](../../mfc/codesnippet/cpp/cmapstringtoob-class_10.cpp)]  
  
 I risultati di questo programma sono come segue:  
  
 `before Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $493C 11`  
  
 `[Bart] = a CAge at $4654 13`  
  
 `after Lisa's birthday: A CMapStringToOb with 2 elements`  
  
 `[Lisa] = a CAge at $49C0 12`  
  
 `[Bart] = a CAge at $4654 13`  
  
## <a name="see-also"></a>Vedere anche  
 [CObject (classe)](../../mfc/reference/cobject-class.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Classe CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)   
 [Classe CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)   
 [Classe CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)   
 [Classe CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)   
 [Classe CMapWordToOb](../../mfc/reference/cmapwordtoob-class.md)   
 [Classe CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)
