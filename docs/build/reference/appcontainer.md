---
title: /APPCONTAINER
ms.date: 11/04/2016
f1_keywords:
- /APPCONTAINER
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
ms.openlocfilehash: eb922a29b00fee63effae302505f25c98b04523e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274027"
---
# <a name="appcontainer"></a>/APPCONTAINER

Contrassegna un eseguibile che deve essere eseguito in un contenitore di app, ad esempio, un'app di Microsoft Store o Windows universale.

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Note

Un file eseguibile per cui è impostata l'opzione **/APPCONTAINER** può essere eseguito solo in un contenitore di app, l'ambiente di isolamento dei processi introdotto in Windows 8. Per le app di Microsoft Store e Windows universale, è necessario impostare questa opzione.

## <a name="see-also"></a>Vedere anche

[Opzioni di EDITBIN](editbin-options.md)<br/>
[Informazioni sulle app di Windows universale](/windows/uwp/get-started/universal-application-platform-guide)
