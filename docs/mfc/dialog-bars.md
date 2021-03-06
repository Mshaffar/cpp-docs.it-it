---
title: Barra di finestra di dialogo
ms.date: 11/19/2018
helpviewer_keywords:
- MFC, control bars
- CDialogBar class [MFC], dialog bars
- control bars [MFC], dialog bars
- dialog bars
- dialog bars [MFC], about dialog bars
ms.assetid: 485c8055-6bb0-4051-8417-dd2971499321
ms.openlocfilehash: e4e843327daba6f0aa468cb07394165bc70fa7f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389623"
---
# <a name="dialog-bars"></a>Barra di finestra di dialogo

Una barra di finestra di dialogo è una barra degli strumenti, un tipo di [sulla barra di controllo](../mfc/control-bars.md) che può contenere qualsiasi tipo di controllo. Poiché presenta le caratteristiche di una finestra di dialogo non modale, una [CDialogBar](../mfc/reference/cdialogbar-class.md) oggetto fornisce una barra degli strumenti più potente.

Esistono alcune differenze principali tra una barra degli strumenti e un `CDialogBar` oggetto. Oggetto `CDialogBar` oggetto viene creato da una risorsa modello di finestra, che è possibile creare tramite l'editor di finestre di Visual C++ e che può contenere qualsiasi tipo di controllo di Windows. L'utente può spostarsi dal controllo del codice al controllo. Ed è possibile specificare uno stile di allineamento per allineare la barra di finestra di dialogo con qualsiasi parte della finestra cornice padre o anche per lasciare posto se l'elemento padre viene ridimensionato. Nella figura seguente mostra una barra di finestra di dialogo con un'ampia gamma di controlli.

![Barra di finestra di dialogo VC](../mfc/media/vc378t1.gif "barra finestra di dialogo VC") <br/>
Una barra di finestra di dialogo

Per gli altri aspetti, utilizzo di un `CDialogBar` oggetto è, ad esempio l'utilizzo di una finestra di dialogo non modale. Usare l'editor finestre per progettare e creare la risorsa finestra di dialogo.

Uno delle lodi della barra della finestra è che possono includere controlli diversi da pulsanti.

Anche se è normale per derivare le classi di finestra di dialogo da `CDialog`, non è in genere derivare una classe personalizzata per una barra di finestra di dialogo. Le barre di finestra di dialogo sono estensioni per una finestra principale ed eventuali messaggi di notifica del controllo barra di finestra di dialogo, ad esempio **BN_CLICKED** oppure **EN_CHANGE**, verrà inviato all'elemento padre della finestra di dialogo barra, la finestra principale.

## <a name="see-also"></a>Vedere anche

[Elementi dell'interfaccia utente](../mfc/user-interface-elements-mfc.md)<br/>
[Esempio](../overview/visual-cpp-samples.md)
