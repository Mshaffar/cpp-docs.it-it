---
title: AsWeak (funzione)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 1332aa140a8298590ad83158e0ec1b75035c4e92
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785244"
---
# <a name="asweak-function"></a>AsWeak (funzione)

Recupera un riferimento debole a un'istanza specificata.

## <a name="syntax"></a>Sintassi

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Un puntatore al tipo del parametro *p*.

*p*<br/>
Un'istanza di un tipo.

*pWeak*<br/>
Al termine di questa operazione, un puntatore a un riferimento debole al parametro *p*.

## <a name="return-value"></a>Valore restituito

S_OK, se questa operazione ha esito positivo; in caso contrario, un errore HRESULT che indica la causa dell'errore.

## <a name="requirements"></a>Requisiti

**Intestazione:** client.h

**Spazio dei nomi:** Microsoft::WRL

## <a name="see-also"></a>Vedere anche

[Spazio dei nomi Microsoft::WRL](microsoft-wrl-namespace.md)