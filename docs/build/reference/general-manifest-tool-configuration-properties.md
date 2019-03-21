---
title: Proprietà di configurazione dello strumento manifesto (commenti relativi alla documentazione di C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
ms.openlocfilehash: 9acdb7f5c934a8cabdd1803074778ac9f01f4960
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827769"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>Generale, Strumento Manifesto, Proprietà di configurazione, finestra di dialogo Pagine delle proprietà di &lt;nomeprogetto&gt;

Usare questa finestra di dialogo per specificare opzioni generali per [Mt.exe](https://msdn.microsoft.com/library/aa375649).

Per accedere alla finestra di dialogo di questa pagina delle proprietà, aprire le pagine delle proprietà per il progetto o la finestra delle proprietà. Espandere il nodo **Strumento Manifesto** in **Proprietà di configurazione**, quindi selezionare **Generale**.

## <a name="uielement-list"></a>Elenco UIElement

- **Non visualizzare messaggio di avvio**

   **Sì (/nologo)** specifica che le informazioni standard sul copyright Microsoft non verranno visualizzate quando sarà avviato lo strumento Manifesto. Usare questa opzione per non visualizzare l'output indesiderato nei file di log, quando si esegue mt.exe come parte di un processo di compilazione o da un ambiente di compilazione.

- **Output dettagliato**

   **Sì (/verbose)** specifica che le informazioni di compilazione aggiuntive verranno visualizzate durante la generazione del manifesto.

- **Identità assembly**

   Usa l'opzione /identity per specificare una stringa di identità, che contiene gli attributi per [\<assemblyIdentity> Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Una stringa di identità inizia con il valore per l'attributo `name` ed è seguita da *attribute* = *value* pairs. Gli attributi in una stringa di identità sono delimitati dalla virgola.

   Di seguito è riportato un esempio di stringa di identità:

   `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="see-also"></a>Vedere anche

[ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)<br>
[Pagine delle proprietà Strumento Manifesto](manifest-tool-property-pages.md)<br>
[Impostare il compilatore C++ e creare proprietà in Visual Studio](../working-with-project-properties.md)