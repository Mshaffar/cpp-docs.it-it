---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 09/02/2019
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: 3e5ae7f897500775671f8bd2563028874579a627
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221353"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Sezione specifica Microsoft**

Conta il numero di `1` bit (conteggio popolazione) in un Unsigned Integer a 16, 32 o 64 bit.

## <a name="syntax"></a>Sintassi

```C
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

### <a name="parameters"></a>Parametri

*value*\
in Unsigned Integer a 16, 32 o 64 bit per cui si desidera il conteggio della popolazione.

## <a name="return-value"></a>Valore restituito

Numero di `1` bit nel parametro *value* .

## <a name="requirements"></a>Requisiti

|Funzione intrinseca|Architettura|
|---------------|------------------|
|`__popcnt16`|Manipolazione avanzata di bit|
|`__popcnt`|Manipolazione avanzata di bit|
|`__popcnt64`|Manipolazione di bit avanzata in modalità a 64 bit.|

**File di intestazione** \<> intrin. h

## <a name="remarks"></a>Note

Ognuna delle funzioni intrinseche genera l' `popcnt` istruzione. In modalità a 32 bit non sono disponibili registri per utilizzo generico a 64 bit, pertanto 64 bit `popcnt` non è supportato.

Per determinare il supporto hardware per `popcnt` l'istruzione, chiamare `__cpuid` l'oggetto `InfoType=0x00000001` intrinseco con e selezionare `CPUInfo[2] (ECX)`il bit 23 di. Questo bit è 1 se l'istruzione è supportata; in caso contrario, 0. Se si esegue codice che usa queste funzioni intrinseche su hardware che non supporta `popcnt` l'istruzione, i risultati sono imprevedibili.

## <a name="example"></a>Esempio

```cpp
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**Fine sezione specifica Microsoft**

Parti Copyright 2007 by Advanced Micro Devices, Inc. Tutti i diritti sono riservati. Riprodotto con l'autorizzazione da Advanced Micro Devices, Inc.

## <a name="see-also"></a>Vedere anche

[Intrinseci del compilatore](../intrinsics/compiler-intrinsics.md)
