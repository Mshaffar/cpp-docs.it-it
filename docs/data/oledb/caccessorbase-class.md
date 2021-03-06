---
title: Classe CAccessorBase
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 8aef8a04d7adff903e21491a91014d55aab769da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212292"
---
# <a name="caccessorbase-class"></a>Classe CAccessorBase

Tutte le funzioni di accesso nei modelli di OLE DB derivano da questa classe. `CAccessorBase` consente a un set di righe di gestire più funzioni di accesso. Fornisce inoltre un'associazione per i parametri e le colonne di output.

## <a name="syntax"></a>Sintassi

```cpp
// Replace with syntax
```

## <a name="members"></a>Members

### <a name="methods"></a>Metodi

|||
|-|-|
|[Close](#close)|Chiude le funzioni di accesso.|
|[GetHAccessor](#geth)|Recupera l'handle della funzione di accesso.|
|[GetNumAccessors](#getnum)|Recupera il numero di funzioni di accesso create dalla classe.|
|[IsAutoAccessor](#isauto)|Verifica se la funzione di accesso specificata è un autoaccesso.|
|[ReleaseAccessors](#release)|Rilascia le funzioni di accesso.|

## <a name="requirements"></a>Requisiti

**Intestazione:** atldbcli.h

## <a name="caccessorbaseclose"></a><a name="close"></a>CAccessorBase:: Close

Chiude le funzioni di accesso.

### <a name="syntax"></a>Sintassi

```cpp
void Close();
```

### <a name="remarks"></a>Osservazioni

Prima di tutto, è necessario chiamare [ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) .

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a>CAccessorBase:: GetHAccessor

Recupera l'handle di accesso di una funzione di accesso specificata.

### <a name="syntax"></a>Sintassi

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametri

*nAccessor*<br/>
[in] Numero di offset uguale a zero per la funzione di accesso.

### <a name="return-value"></a>Valore restituito

Handle della funzione di accesso.

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a>CAccessorBase:: GetNumAccessors

Recupera il numero di funzioni di accesso create dalla classe.

### <a name="syntax"></a>Sintassi

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Valore restituito

Numero di funzioni di accesso create dalla classe.

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a>CAccessorBase:: IsAutoAccessor

Restituisce true se i dati vengono recuperati automaticamente per la funzione di accesso durante un'operazione di spostamento.

### <a name="syntax"></a>Sintassi

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parametri

*nAccessor*<br/>
[in] Numero di offset uguale a zero per la funzione di accesso.

### <a name="return-value"></a>Valore restituito

Restituisce **true** se la funzione di accesso è un autoaccesso. Negli altri casi, viene restituito **false**.

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a>CAccessorBase:: ReleaseAccessors

Rilascia le funzioni di accesso create dalla classe.

### <a name="syntax"></a>Sintassi

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parametri

*pUnk*<br/>
in Puntatore a un'interfaccia `IUnknown` per l'oggetto COM per il quale sono state create le funzioni di accesso.

### <a name="return-value"></a>Valore restituito

Valore HRESULT standard.

### <a name="remarks"></a>Osservazioni

Chiamata eseguita da [CAccessorRowset:: Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Vedere anche

[Modelli di consumer OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Riferimenti ai modelli consumer OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Classe CAccessorBase](../../data/oledb/caccessorbase-class.md)
