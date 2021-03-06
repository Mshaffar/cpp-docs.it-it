---
title: /APPCONTAINER (UWP/Microsoft Store App)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: f7ab8cf1ce034580953fdf1403264e8ef3d3ff09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295117"
---
# <a name="appcontainer-microsoft-store-app"></a>/APPCONTAINER (App di Microsoft Store)

Specifica se il linker viene creata un'immagine eseguibile che deve essere eseguita in un contenitore di app.

## <a name="syntax"></a>Sintassi

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Note

Per impostazione predefinita, /APPCONTAINER è disattivato.

Questa opzione consente di modificare un file eseguibile per indicare se l'app deve essere eseguito nell'ambiente di isolamento dei processi di appcontainer. Specificare /APPCONTAINER per un'app che deve essere eseguito nell'ambiente appcontainer, ad esempio, un'app Universal Windows Platform (UWP) o Windows Phone 8.x. (L'opzione è impostata automaticamente in Visual Studio quando si crea un'app di Windows universale da un modello.) Per un'app desktop, specificare /appcontainer: No oppure omettere semplicemente l'opzione.

L'opzione /APPCONTAINER è stata introdotta in Windows 8.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Per impostare questa opzione del linker in Visual Studio

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per altre informazioni, vedere [le proprietà del compilatore e compilazione impostare C++ in Visual Studio](../working-with-project-properties.md).

1. Espandere il nodo **Proprietà di configurazione**.

1. Espandere la **Linker** nodo.

1. Selezionare il **riga di comando** pagina delle proprietà.

1. Nelle **opzioni aggiuntive**, immettere `/APPCONTAINER` o `/APPCONTAINER:NO`.

## <a name="see-also"></a>Vedere anche

[Informazioni di riferimento sul linker MSVC](linking.md)<br/>
[Opzioni del linker MSVC](linker-options.md)
