---
title: Operazioni di flusso nei controlli Rich Edit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
ms.openlocfilehash: 73277f59dc0ad4dfe21d481d0b893903ed407ea9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512945"
---
# <a name="stream-operations-in-rich-edit-controls"></a>Operazioni di flusso nei controlli Rich Edit

È possibile utilizzare i flussi per trasferire i dati all'interno o all'esterno di un controllo Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Un flusso è definito da una struttura [EDITSTREAM](/windows/win32/api/richedit/ns-richedit-editstream) , che specifica un buffer e una funzione di callback definita dall'applicazione.

Per leggere i dati in un controllo Rich Edit, ovvero trasmettere i dati in, usare la funzione membro [streamin](../mfc/reference/cricheditctrl-class.md#streamin) . Il controllo chiama ripetutamente la funzione di callback definita dall'applicazione, che trasferisce ogni volta una parte dei dati nel buffer.

Per salvare il contenuto di un controllo Rich Edit, ovvero trasmettere i dati in uscita, è possibile usare la funzione membro di [streaming](../mfc/reference/cricheditctrl-class.md#streamout) . Il controllo scrive ripetutamente al buffer e quindi chiama la funzione di callback definita dall'applicazione. Per ogni chiamata, la funzione di callback salva il contenuto del buffer.

## <a name="see-also"></a>Vedere anche

[Uso di CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controlli](../mfc/controls-mfc.md)
