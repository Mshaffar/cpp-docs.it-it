---
title: /ERRORREPORT (editbin.exe)
description: Informazioni di riferimento sull'opzione della riga di comando/ERRORREPORT dell'utilità Microsoft EDITBIN).
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_editbin
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 4456a49cc53b21bd24c616852159ca299181071b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439908"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> L'opzione/ERRORREPORT è deprecata. A partire da Windows Vista, la segnalazione degli errori è controllata dalle impostazioni di [segnalazione errori Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Sintassi

> **/Errorreport** \[ **NONE** \| **prompt** \| **coda** \| **Send** ]

## <a name="remarks"></a>Osservazioni

Gli argomenti **/errorreport** vengono sottoposti a override dalle impostazioni del servizio Segnalazione errori Windows. EDITBIN) Invia automaticamente i report degli errori interni a Microsoft, se la creazione di report è abilitata da Segnalazione errori Windows. Non viene inviato alcun report se disabilitato da Segnalazione errori Windows.

## <a name="see-also"></a>Vedere anche

[Opzioni di EDITBIN](editbin-options.md)
