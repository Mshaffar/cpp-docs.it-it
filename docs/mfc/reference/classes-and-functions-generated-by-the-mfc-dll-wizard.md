---
title: Classi e funzioni generate dalla Creazione guidata DLL MFC
ms.date: 11/04/2016
helpviewer_keywords:
- functions [MFC]
- functions [MFC], DLLs
- MFC DLL Wizard
- DLLs [MFC], wizard classes and functions
- classes [MFC], generated by MFC DLL wizard
- code [MFC], generated by MFC DLL wizard
ms.assetid: e69e62fe-4953-42bf-a2fc-50bbf9bdaeaf
ms.openlocfilehash: add914f18ab961ff6dbc5cb056e2f2a81c252a48
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754916"
---
# <a name="classes-and-functions-generated-by-the-mfc-dll-wizard"></a>Classi e funzioni generate dalla Creazione guidata DLL MFC

Il codice generato dalla Creazione guidata DLL MFC dipende dal tipo di DLL che si sta creando e dalle opzioni selezionate. La Creazione guidata DLL MFC genera lo stesso codice per entrambi i form delle DLL MFC regolari.

|Tipo di DLL|Opzione|Classi|Funzioni|
|-----------------|------------|-------------|---------------|
|[Estensione](../../build/extension-dlls-overview.md)|nessuno|nessuno|`DllMain`|
|[Regular](../../build/regular-dlls-dynamically-linked-to-mfc.md)|nessuno|Classe di applicazione derivata da`CWinApp`|nessuno|
|[Regular](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Automazione|Classe di applicazione derivata da`CWinApp`|`DllGetClassObject` `DllCanUnloadNow` `DllRegisterServer`|
|[Estensione](../../build/extension-dlls-overview.md)|Socket di finestra|nessuno|`DllMain`|
|[Regular](../../build/regular-dlls-dynamically-linked-to-mfc.md)|Socket di finestra|Classe di applicazione derivata da`CWinApp`|`InitInstance`contiene una chiamata a`AfxSocketInit`|

## <a name="see-also"></a>Vedere anche

[Procedura guidata DLL MFC](../../mfc/reference/mfc-dll-wizard.md)
