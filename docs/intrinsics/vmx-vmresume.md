---
title: __vmx_vmresume
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: 34d0e6814dd00da07076e644513400bd5be36bd3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219448"
---
# <a name="__vmx_vmresume"></a>__vmx_vmresume

**Sezione specifica Microsoft**

Riprende l'operazione non radice VMX usando la struttura di controllo della macchina virtuale corrente (VMCS, Virtual machine Control Structure).

## <a name="syntax"></a>Sintassi

```C
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>Valore restituito

|Valore|Significato|
|-----------|-------------|
|0|Operazione completata.|
|1|Operazione non riuscita con stato esteso disponibile in `VM-instruction error field` della VMCS corrente.|
|2|Operazione non riuscita senza stato disponibile.|

## <a name="remarks"></a>Note

Un'applicazione può eseguire un'operazione di accesso VM con la funzione [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) o `__vmx_vmresume` . La funzione `__vmx_vmlaunch` può essere usata solo con una VMCS il cui stato di avvio è `Clear`e la funzione `__vmx_vmresume` può essere usata solo con una VMCS il cui stato di avvio è `Launched`. Di conseguenza, usare la funzione [__vmx_vmclear](../intrinsics/vmx-vmclear.md) per impostare lo stato di avvio di una VMCS su `Clear`e quindi usare la funzione `__vmx_vmlaunch` per la prima operazione di accesso VM e la funzione `__vmx_vmresume` per le operazioni di accesso VM successive.

La funzione `__vmx_vmresume` è equivalente alle `VMRESUME` istruzioni in linguaggio macchina. Questa funzione supporta l'interazione di monitoraggio della macchina virtuale di un host con un sistema operativo guest e le relative applicazioni. Per altre informazioni, cercare il documento PDF sulle specifiche tecniche di virtualizzazione Intel per l'architettura Intel IA-32, numero documento C97063-002 sul sito [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Requisiti

|Funzione intrinseca|Architettura|
|---------------|------------------|
|`__vmx_vmresume`|X64|

**File di intestazione** \<> intrin. h

**Fine sezione specifica Microsoft**

## <a name="see-also"></a>Vedere anche

[Intrinseci del compilatore](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
