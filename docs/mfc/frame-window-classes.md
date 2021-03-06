---
title: Classi Frame-Window
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: d42fa475fca7c92e4ba46b164a9beda9869231c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219782"
---
# <a name="frame-window-classes"></a>Classi Frame-Window

Ogni applicazione dispone di una "finestra cornice principale," una finestra del desktop in genere con il nome dell'applicazione nella barra del titolo. Ogni documento è in genere una "finestra cornice di documento". Una finestra cornice di documento contiene almeno una visualizzazione, che presenta i dati del documento.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Windows frame in applicazioni SDI e MDI

Per un'applicazione SDI, è disponibile una finestra cornice derivata dalla classe [CFrameWnd](../mfc/reference/cframewnd-class.md). In questa finestra è la finestra cornice principale sia la finestra cornice di documento. Per un'applicazione MDI, la finestra cornice principale è derivata dalla classe [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), e le finestre cornice del documento, che sono finestre figlio MDI, derivate dalla classe [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Usare la classe di finestre cornice o derivare da esso

Queste classi forniscono la maggior parte delle funzionalità della finestra cornice che è necessario per le applicazioni. In circostanze normali, il comportamento predefinito e l'aspetto che forniscono adatta alle proprie esigenze. Se risultano necessarie funzionalità aggiuntive, derivano da queste classi.

### <a name="what-do-you-want-to-know-more-about"></a>Ciò che si desidera saperne di più

- [Classi frame-window create dalla procedura guidata dell'applicazione](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [Stili frame-window](../mfc/frame-window-styles-cpp.md)

- [Modifica degli stili di una finestra creata da MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Vedere anche

[Finestre cornice](../mfc/frame-windows.md)
