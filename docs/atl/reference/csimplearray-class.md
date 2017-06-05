---
title: Classe CSimpleArray | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
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
ms.openlocfilehash: e261f95a375a2edda1d543a36b605d23fc718b99
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="csimplearray-class"></a>Classe CSimpleArray
Questa classe fornisce metodi per la gestione di una matrice semplice.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>  
class CSimpleArray
```  
  
#### <a name="parameters"></a>Parametri  
 `T`  
 Il tipo di dati da archiviare nella matrice.  
  
 `TEqual`  
 Un oggetto di tratto, che definisce il test di uguaglianza per gli elementi di tipo `T`.  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CSimpleArray::CSimpleArray](#csimplearray)|Il costruttore per la matrice semplice.|  
|[CSimpleArray:: ~ CSimpleArray](#dtor)|Il distruttore per la matrice semplice.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CSimpleArray::Add](#add)|Aggiunge un nuovo elemento nella matrice.|  
|[CSimpleArray::Find](#find)|Trova un elemento nella matrice.|  
|[CSimpleArray::GetData](#getdata)|Restituisce un puntatore ai dati archiviati nella matrice.|  
|[CSimpleArray::GetSize](#getsize)|Restituisce il numero di elementi archiviati nella matrice.|  
|[CSimpleArray::Remove](#remove)|Rimuove un elemento specificato della matrice.|  
|[CSimpleArray::RemoveAll](#removeall)|Rimuove tutti gli elementi della matrice.|  
|[CSimpleArray::RemoveAt](#removeat)|Rimuove l'elemento specificato della matrice.|  
|[CSimpleArray::SetAtIndex](#setatindex)|Imposta l'elemento specificato nella matrice.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CSimpleArray::operator\[\]](#operator_at)|Recupera un elemento da una matrice.|  
|[CSimpleArray::operator =](#operator_eq)|Operatore di assegnazione.|  

  
## <a name="remarks"></a>Note  
 `CSimpleArray`fornisce metodi per la creazione e gestione di una semplice matrice di un determinato tipo `T`.  
  
 Il parametro `TEqual` consente di definire una funzione di uguaglianza di due elementi di tipo `T`. Creando una classe simile a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md), è possibile modificare il comportamento del test di uguaglianza per qualsiasi matrice specificata. Ad esempio, quando si lavora con una matrice di puntatori, può risultare utile definire l'uguaglianza come a seconda dei valori che di puntatori di riferimento. L'implementazione predefinita utilizza **operator=()**.  
  
 Entrambi `CSimpleArray` e [CSimpleMap](../../atl/reference/csimplemap-class.md) sono progettati per un numero ridotto di elementi. [CAtlArray](../../atl/reference/catlarray-class.md) e [CAtlMap](../../atl/reference/catlmap-class.md) deve essere utilizzata quando la matrice contiene un numero elevato di elementi.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** atlsimpcoll. h  
  
## <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATL_Utilities&#86;](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]  
  
##  <a name="add"></a>CSimpleArray::Add  
 Aggiunge un nuovo elemento nella matrice.  
  
```
BOOL Add(const T& t);
```  
  
### <a name="parameters"></a>Parametri  
 *t*  
 Elemento da aggiungere alla matrice.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce TRUE se l'elemento è stato aggiunto alla matrice, FALSE in caso contrario.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATL_Utilities&#87;](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]  
  
##  <a name="csimplearray"></a>CSimpleArray::CSimpleArray  
 Il costruttore dell'oggetto matrice.  
  
```
CSimpleArray(const CSimpleArray<T, TEqual>& src);  
CSimpleArray();
```     
  
### <a name="parameters"></a>Parametri  
 *src*  
 Oggetto `CSimpleArray` esistente.  
  
### <a name="remarks"></a>Note  
 Inizializza i membri di dati, creazione di una nuova classe vuota `CSimpleArray` oggetto o una copia di un oggetto esistente `CSimpleArray` oggetto.  
  
##  <a name="dtor"></a>CSimpleArray:: ~ CSimpleArray  
 Distruttore.  
  
```
~CSimpleArray();
```  
  
### <a name="remarks"></a>Note  
 Libera tutte le risorse allocate.  
  
##  <a name="find"></a>CSimpleArray::Find  
 Trova un elemento nella matrice.  
  
```
int Find(const T& t) const;
```  
  
### <a name="parameters"></a>Parametri  
 *t*  
 L'elemento da cercare.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce l'indice dell'elemento trovato o -1 se l'elemento non viene trovato.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATL_Utilities&#88;](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]  
  
##  <a name="getdata"></a>CSimpleArray::GetData  
 Restituisce un puntatore ai dati archiviati nella matrice.  
  
```
T* GetData() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce un puntatore ai dati nella matrice.  
  
##  <a name="getsize"></a>CSimpleArray::GetSize  
 Restituisce il numero di elementi archiviati nella matrice.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce il numero di elementi archiviati nella matrice.  
  
##  <a name="operator_at"></a>CSimpleArray::operator\[\]  
 Recupera un elemento da una matrice.  
  
```
T& operator[](int nindex);
```  
  
### <a name="parameters"></a>Parametri  
 `nIndex`  
 L'indice di elemento.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce l'elemento della matrice cui fa riferimento `nIndex`.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATL_Utilities&#89;](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]  
  
##  <a name="operator_eq"></a>CSimpleArray::operator =  
 Operatore di assegnazione.  
  
```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```  
  
### <a name="parameters"></a>Parametri  
 *src*  
 Matrice da copiare.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce un puntatore a aggiornato `CSimpleArray` oggetto.  
  
### <a name="remarks"></a>Note  
 Copia tutti gli elementi dal `CSimpleArray` oggetto a cui fa riferimento *src* nell'oggetto matrice corrente, sostituendo tutti i dati esistenti.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATL_Utilities&#90;](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]  
  
##  <a name="remove"></a>CSimpleArray::Remove  
 Rimuove un elemento specificato della matrice.  
  
```
BOOL Remove(const T& t);
```  
  
### <a name="parameters"></a>Parametri  
 *t*  
 Elemento da rimuovere dalla matrice.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce TRUE se l'elemento viene trovato e rimosso, FALSE in caso contrario.  
  
### <a name="remarks"></a>Note  
 Quando un elemento viene rimosso, gli elementi rimanenti della matrice vengono numerati per riempire lo spazio vuoto.  
  
##  <a name="removeall"></a>CSimpleArray::RemoveAll  
 Rimuove tutti gli elementi della matrice.  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>Note  
 Rimuove tutti gli elementi attualmente archiviati nella matrice.  
  
##  <a name="removeat"></a>CSimpleArray::RemoveAt  
 Rimuove l'elemento specificato della matrice.  
  
```
BOOL RemoveAtint nIndex);
```  
  
### <a name="parameters"></a>Parametri  
 `nIndex`  
 Indice che punta all'elemento da rimuovere.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce TRUE se l'elemento è stato rimosso, FALSE se l'indice non è valido.  
  
### <a name="remarks"></a>Note  
 Quando un elemento viene rimosso, gli elementi rimanenti della matrice vengono numerati per riempire lo spazio vuoto.  
  
##  <a name="setatindex"></a>CSimpleArray::SetAtIndex  
 Impostare l'elemento specificato nella matrice.  
  
```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```  
  
### <a name="parameters"></a>Parametri  
 `nIndex`  
 L'indice dell'elemento da modificare.  
  
 *t*  
 Valore da assegnare all'elemento specificato.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce TRUE se ha esito positivo, FALSE se l'indice non è valido.  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari sulla classe](../../atl/atl-class-overview.md)
