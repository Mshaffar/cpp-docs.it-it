---
title: Classi di finestre cornice (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 3e56bd0f449992118db75a44c39b6e0e15cb0d86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392793"
---
# <a name="frame-window-classes-windows"></a>Classi di finestre cornice (Windows)

Finestre cornice sono finestre cornice intorno a un'applicazione o una parte di un'applicazione. Finestre cornice in genere contengono altre finestre, ad esempio viste, le barre degli strumenti e le barre di stato. Nel caso del `CMDIFrameWnd`, possono contenere `CMDIChildWnd` oggetti indirettamente.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Classe di base per la finestra cornice principale di un'applicazione SDI. Anche la classe base per tutte le altre classi finestra cornice.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Classe di base per la finestra cornice principale di un'applicazione MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
La classe base per finestre cornice del documento di un'applicazione MDI.

[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)<br/>
Una finestra cornice di mezza altezza generalmente visualizzata in barre degli strumenti mobili.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Fornisce la finestra cornice per una visualizzazione quando viene modificato un documento del server sul posto.

## <a name="related-class"></a>Classe correlata

Classe `CMenu` fornisce un'interfaccia tramite cui si desidera accedere ai menu dell'applicazione. È utile per la gestione dei menu in modo dinamico in fase di esecuzione; ad esempio, durante l'aggiunta o eliminazione di voci di menu in base al contesto. Anche se i menu vengono spesso usati con finestre cornice, possono anche essere utilizzati con le finestre di dialogo e altre finestre non figlio.

[CMenu](../mfc/reference/cmenu-class.md)<br/>
Incapsula un `HMENU` handle alla barra dei menu e menu di scelta rapida dell'applicazione.

## <a name="see-also"></a>Vedere anche

[Panoramica della classe](../mfc/class-library-overview.md)
