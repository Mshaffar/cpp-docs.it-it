---
title: InterfaceTraits (struttura)
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58785497"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits (struttura)

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

## <a name="syntax"></a>Sintassi

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Parametri

*I0*<br/>
Il nome di un'interfaccia.

*CloakedType*<br/>
Per la `RuntimeClass`, `Implements` e `ChainInterfaces`, un'interfaccia che non sarà nell'elenco di ID di interfaccia è supportata.

## <a name="remarks"></a>Note

Caratteristiche comuni implementa un'interfaccia.

Il secondo modello è una specializzazione per interfacce mascherate. Il terzo modello è una specializzazione per i parametri di tipo Nil.

## <a name="members"></a>Membri

### <a name="public-typedefs"></a>TypeDef pubblici

Nome   | Descrizione
------ | ------------------------------------------
`Base` | Un sinonimo per il *I0* parametro di modello.

### <a name="public-methods"></a>Metodi pubblici

Nome                                                   | Descrizione
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Indica se il puntatore specificato può essere convertito in un puntatore a `Base`.
[InterfaceTraits::CastToBase](#casttobase)             | Viene eseguito il cast il puntatore specificato a un puntatore a `Base`.
[InterfaceTraits::CastToUnknown](#casttounknown)       | Viene eseguito il cast il puntatore specificato a un puntatore a `IUnknown`.
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | Assegna l'ID dell'interfaccia `Base` all'elemento della matrice specificata dall'argomento dell'indice.
[InterfaceTraits::Verify](#verify)                     | Verifica che `Base` viene derivato correttamente.

### <a name="public-constants"></a>Costanti pubbliche

Nome                                   | Descrizione
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Contiene il numero ID associato all'oggetto corrente di interfaccia `InterfaceTraits` oggetto.

## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà

`InterfaceTraits`

## <a name="requirements"></a>Requisiti

**Intestazione:** Implements. h

**Spazio dei nomi:** Microsoft::WRL::Details

## <a name="cancastto"></a>InterfaceTraits::CanCastTo

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametri

*ptr*<br/>
Il nome di un puntatore a un tipo.

*riid*<br/>
ID dell'interfaccia `Base`.

*ppv*<br/>
Se questa operazione ha esito positivo, *ppv* punta a un'interfaccia specificata da `Base`. In caso contrario, *ppv* è impostata su `nullptr`.

### <a name="return-value"></a>Valore restituito

**true** se questa operazione ha esito positivo e *ptr* viene eseguito il cast a un puntatore al `Base`; in caso contrario, **false**.

### <a name="remarks"></a>Note

Indica se il puntatore specificato può essere convertito in un puntatore a `Base`.

Per altre informazioni sulle `Base`, vedere la [typedef pubblici](#public-typedefs) sezione.

## <a name="casttobase"></a>InterfaceTraits::CastToBase

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Il tipo del parametro *ptr*.

*ptr*<br/>
Puntatore a un tipo *T*.

### <a name="return-value"></a>Valore restituito

Un puntatore a `Base`.

### <a name="remarks"></a>Note

Viene eseguito il cast il puntatore specificato a un puntatore a `Base`.

Per altre informazioni sulle `Base`, vedere la [typedef pubblici](#public-typedefs) sezione.

## <a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametri

*T*<br/>
Il tipo del parametro *ptr*.

*ptr*<br/>
Puntatore al tipo *T*.

### <a name="return-value"></a>Valore restituito

Puntatore per l'interfaccia IUnknown da cui `Base` derivato.

### <a name="remarks"></a>Note

Viene eseguito il cast il puntatore specificato a un puntatore a `IUnknown`.

Per altre informazioni sulle `Base`, vedere la [typedef pubblici](#public-typedefs) sezione.

## <a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametri

*index*<br/>
Puntatore a un campo che contiene un valore di indice in base zero.

*iids*<br/>
Matrice ID di interfaccia.

### <a name="remarks"></a>Note

Assegna l'ID dell'interfaccia `Base` all'elemento della matrice specificata dall'argomento dell'indice.

Diversamente dal nome di questa API, un solo array è stato modificato; non l'intera matrice.

Per altre informazioni sulle `Base`, vedere la [typedef pubblici](#public-typedefs) sezione.

## <a name="iidcount"></a>InterfaceTraits::IidCount

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Note

Contiene il numero ID associato all'oggetto corrente di interfaccia `InterfaceTraits` oggetto.

## <a name="verify"></a>InterfaceTraits::Verify

Supporta l'infrastruttura WRL e non deve essere usato direttamente dal codice.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Note

Verifica che `Base` viene derivato correttamente.

Per altre informazioni sulle `Base`, vedere la [typedef pubblici](#public-typedefs) sezione.