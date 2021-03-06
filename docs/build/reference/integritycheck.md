---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: 4174e22dcdadb3b3319998614285c13741fe3a88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269765"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Specifica che la firma digitale di immagine binari deve essere controllata in fase di caricamento.

> **/INTEGRITYCHECK**[**:NO**]

## <a name="remarks"></a>Note

Nell'intestazione del file DLL o del file eseguibile, questa opzione imposta un flag che richiede una verifica della firma digitale dal gestore della memoria per caricare l'immagine in Windows. Le versioni di Windows precedenti a Windows Vista ignorano questo flag. Questa opzione deve essere impostata per le DLL a 64 bit che implementano il codice in modalità kernel ed sono consigliate per tutti i driver di dispositivo. Per altre informazioni, vedere [requisiti di firma del codice in modalità Kernel](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Vedere anche

[Opzioni di EDITBIN](editbin-options.md)
