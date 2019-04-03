---
title: IsSame (struttura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
- internal/Microsoft::WRL::Details::IsSame::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsSame structure
- Microsoft::WRL::Details::IsSame::value constant
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
ms.openlocfilehash: b659f832756b79289181db34fa8d6fc0d974609d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785489"
---
# <a name="issame-structure"></a>IsSame (struttura)

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

## <a name="syntax"></a>Sintassi

```cpp
template <typename T1, typename T2>
struct IsSame;

template <typename T1>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>Parametri

*T1*<br/>
Tipo.

*T2*<br/>
Un altro tipo.

## <a name="remarks"></a>Note

Consente di verificare se un tipo specificato è uguale a un altro tipo specificato.

## <a name="members"></a>Membri

### <a name="public-constants"></a>Costanti pubbliche

Nome                    | Descrizione
----------------------- | --------------------------------------------------
[IsSame::value](#value) | Indica se un tipo è uguale a un altro.

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`IsSame`

## <a name="requirements"></a>Requisiti

**Intestazione:** FTM

**Spazio dei nomi:** Microsoft::WRL::Details

## <a name="value"></a>IsSame::value

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

```cpp
template <typename T1, typename T2>
struct IsSame
{
    static const bool value = false;
};

template <typename T1>
struct IsSame<T1, T1>
{
    static const bool value = true;
};
```

### <a name="remarks"></a>Note

Indica se un tipo è uguale a un altro.

`value` viene **true** se i parametri del modello sono gli stessi, e **false** se i parametri del modello sono diversi.