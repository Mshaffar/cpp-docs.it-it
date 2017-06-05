---
title: Classe multi_link_registry | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
dev_langs:
- C++
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: b52ee20ed16a4ce8d0b9f11b6acf25112464b49b
ms.contentlocale: it-it
ms.lasthandoff: 03/17/2017

---
# <a name="multilinkregistry-class"></a>Classe multi_link_registry
L'oggetto `multi_link_registry` è un `network_link_registry` che gestisce più blocchi di origine o più blocchi di destinazione.  
  
## <a name="syntax"></a>Sintassi  
  
```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parametri  
 `_Block`  
 Tipo di dati di blocco memorizzato nel `multi_link_registry` oggetto.  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[multi_link_registry](#ctor)|Costruisce un oggetto `multi_link_registry`.|  
|[~ multi_link_registry distruttore](#dtor)|Elimina il `multi_link_registry` oggetto.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[add](#add)|Aggiunge un collegamento per il `multi_link_registry` oggetto. (Esegue l'override di [network_link_registry:: Add](network-link-registry-class.md#add).)|  
|[begin](#begin)|Restituisce un iteratore al primo elemento di `multi_link_registry` oggetto. (Esegue l'override di [network_link_registry:: Begin](network-link-registry-class.md#begin).)|  
|[contiene](#contains)|Ricerche di `multi_link_registry` oggetto per un blocco specificato. (Esegue l'override di [network_link_registry:: Contains](network-link-registry-class.md#contains).)|  
|[count](#count)|Conta il numero di elementi di `multi_link_registry` oggetto. (Esegue l'override di [network_link_registry:: Count](network-link-registry-class.md#count).)|  
|[remove](#remove)|Rimuove un collegamento di `multi_link_registry` oggetto. (Esegue l'override di [network_link_registry:: Remove](network-link-registry-class.md#remove).)|  
|[set_bound](#set_bound)|Imposta un limite superiore al numero di collegamenti di `multi_link_registry` oggetto può contenere.|  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [network_link_registry](network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** agents.h  
  
 **Spazio dei nomi:** Concurrency  
  
##  <a name="add"></a>aggiungere 

 Aggiunge un collegamento per il `multi_link_registry` oggetto.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parametri  
 `_Link`  
 Un puntatore a un blocco da aggiungere.  
  
### <a name="remarks"></a>Note  
 Il metodo genera un [invalid_link_target](invalid-link-target-class.md) eccezione se il collegamento è già presente nel Registro di sistema o se un'associazione è già stata impostata con il `set_bound` (funzione) e un collegamento è stato rimosso.  
  
##  <a name="begin"></a>iniziare 

 Restituisce un iteratore al primo elemento di `multi_link_registry` oggetto.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Valore restituito  
 Iteratore che punta al primo elemento di `multi_link_registry` oggetto.  
  
### <a name="remarks"></a>Note  
 Lo stato finale è indicato da un `NULL` collegamento.  
  
##  <a name="contains"></a>contiene 

 Ricerche di `multi_link_registry` oggetto per un blocco specificato.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parametri  
 `_Link`  
 Un puntatore a un blocco che deve essere cercata nel `multi_link_registry` oggetto.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il blocco specificato è stato trovato, `false` in caso contrario.  
  
##  <a name="count"></a>conteggio 

 Conta il numero di elementi di `multi_link_registry` oggetto.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di elementi di `multi_link_registry` oggetto.  
  
##  <a name="ctor"></a>multi_link_registry 

 Costruisce un oggetto `multi_link_registry`.  
  
```
multi_link_registry();
```  
  
##  <a name="dtor"></a>~ multi_link_registry 

 Elimina il `multi_link_registry` oggetto.  
  
```
virtual ~multi_link_registry();
```  
  
### <a name="remarks"></a>Note  
 Il metodo genera un [invalid_operation](invalid-operation-class.md) eccezione se viene chiamato prima che vengano rimossi tutti i collegamenti.  
  
##  <a name="remove"></a>rimuovere 

 Rimuove un collegamento di `multi_link_registry` oggetto.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parametri  
 `_Link`  
 Un puntatore a un blocco deve essere rimosso, se trovato.  
  
### <a name="return-value"></a>Valore restituito  
 `true`Se il collegamento è stato trovato e rimosso, `false` in caso contrario.  
  
##  <a name="set_bound"></a>set_bound 

 Imposta un limite superiore al numero di collegamenti di `multi_link_registry` oggetto può contenere.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parametri  
 `_MaxLinks`  
 Il numero massimo di collegamenti che il `multi_link_registry` oggetto può contenere.  
  
### <a name="remarks"></a>Note  
 Una volta impostato un limite, lo scollegamento di una voce comporta l'impostazione dello stato non modificabile per l'oggetto `multi_link_registry`, pertanto tramite le chiamate successive a `add` verrà generata un'eccezione `invalid_link_target`.  
  
## <a name="see-also"></a>Vedere anche  
 [concorrenza Namespace](concurrency-namespace.md)   
 [Classe single_link_registry](single-link-registry-class.md)
