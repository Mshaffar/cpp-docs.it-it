---
title: Interfaccia ICommandUI | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
dev_langs: C++
helpviewer_keywords: ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4971ceaea57b91ff708315a2c32c7bac2801798f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="icommandui-interface"></a>Interfaccia ICommandUI
Gestisce i comandi dell'interfaccia utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
interface class ICommandUI  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[icommandui__Check](#check)|Imposta l'elemento dell'interfaccia utente per questo comando lo stato di controllo appropriate.|  
|[ICommandUI::ContinueRouting](#continuerouting)|Indica il meccanismo di routing di comandi per continuare il routing del messaggio corrente lungo la catena dei gestori.|  
|[ICommandUI::Enabled](#enabled)|Abilita o disabilita l'elemento dell'interfaccia utente per questo comando.|  
|[ICommandUI::ID](#id)|Ottiene l'ID dell'oggetto di interfaccia utente rappresentato dal `ICommandUI` oggetto.|  
|[ICommandUI::Index](#index)|Ottiene l'indice dell'oggetto di interfaccia utente rappresentato dal `ICommandUI` oggetto.|  
|[ICommandUI::Radio](#radio)|Imposta l'elemento dell'interfaccia utente per questo comando lo stato di controllo appropriate.|  
|[ICommandUI::Text](#text)|Imposta il testo dell'elemento dell'interfaccia utente per questo comando.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia fornisce metodi e proprietà che gestiscono i comandi dell'interfaccia utente. `ICommandUI`è simile a [CCmdUI (classe)](../../mfc/reference/ccmdui-class.md), ad eccezione del fatto che `ICommandUI` viene utilizzato per le applicazioni MFC che interagiscono con i componenti .NET.  
  
 `ICommandUI`viene utilizzato all'interno di un `ON_UPDATE_COMMAND_UI` gestore in un [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-classe derivata. Quando un utente di un'applicazione attiva (Seleziona o fa clic su) un menu, ogni voce di menu viene visualizzato come abilitato o disabilitato. La destinazione di ogni comando di menu fornisce queste informazioni mediante l'implementazione di un `ON_UPDATE_COMMAND_UI` gestore. Per ognuno degli oggetti dell'interfaccia utente comando nell'applicazione, utilizzare la finestra proprietà per creare una voce nella mappa messaggi e un prototipo di funzione per ogni gestore.  
  
 Per ulteriori informazioni su come l'oggetto `ICommandUI` interfaccia viene utilizzata per il routing dei comandi, vedere [procedura: aggiungere comandi (Routing) per il controllo Windows Form](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).  
  
 Per ulteriori informazioni sull'utilizzo di Windows Form, vedere [utilizzando un controllo utente Windows Form in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Per ulteriori informazioni su come vengono gestiti i comandi dell'interfaccia utente in MFC, vedere [CCmdUI (classe)](../../mfc/reference/ccmdui-class.md).  
  
## <a name="check"></a>ICommandUI::Check  
Imposta l'elemento dell'interfaccia utente per questo comando lo stato di controllo appropriate.
```
property UICheckState Check;
```
## <a name="remarks"></a>Note  
Questa proprietà imposta l'elemento dell'interfaccia utente per questo comando per lo stato di controllo appropriate. Impostare controllo sui valori seguenti:  
- Deselezionare 0  
- 1 controllo  
- 2 impostato indeterminato  

## <a name="continuerouting"></a>ICommandUI::ContinueRouting   
Indica il meccanismo di instradamento continuare routing del messaggio corrente lungo la catena di gestori di comando.
```
void ContinueRouting();
```
## <a name="remarks"></a>Note
Si tratta di una funzione membro avanzata che deve essere utilizzata in combinazione con un gestore ON_COMMAND_EX che restituisce FALSE. Per ulteriori informazioni, vedere tecniche nota TN006: mappe messaggi.

## <a name="enabled"></a>ICommandUI::Enabled 
Abilita o disabilita l'elemento dell'interfaccia utente per questo comando.
```
property bool Enabled;
```
## <a name="remarks"></a>Note
Questa proprietà Abilita o disabilita l'elemento dell'interfaccia utente per questo comando. Impostare Enabled su true per abilitare l'elemento, FALSE per disabilitarla.

## <a name="id"></a>ICommandUI::ID  
Ottiene l'ID dell'oggetto di interfaccia utente rappresentato dall'oggetto ICommandUI.
```
property unsigned int ID;
```
## <a name="remarks"></a>Note
Questa proprietà ottiene l'ID (handle) della voce di menu, il pulsante della barra degli strumenti o altro oggetto dell'interfaccia utente rappresentato dall'oggetto ICommandUI.

## <a name="index"></a>ICommandUI::Index   
Ottiene l'indice dell'oggetto di interfaccia utente rappresentato dall'oggetto ICommandUI.
```
property unsigned int Index;
```
## <a name="remarks"></a>Note
Questa proprietà ottiene l'indice (handle) della voce di menu, il pulsante della barra degli strumenti o altro oggetto dell'interfaccia utente rappresentato dall'oggetto ICommandUI.

## <a name="radio"></a>ICommandUI::Radio 
Imposta l'elemento dell'interfaccia utente per questo comando lo stato di controllo appropriate.
```
property bool Radio;
```
## <a name="remarks"></a>Note
Questa proprietà imposta l'elemento dell'interfaccia utente per questo comando per lo stato di controllo appropriate. Opzione insieme a true per abilitare l'elemento. in caso contrario FALSE.

## <a name="text"></a>ICommandUI::Text 
Imposta il testo dell'elemento dell'interfaccia utente per questo comando.
```
property String^ Text;
```
## <a name="remarks"></a>Note
Questa proprietà imposta il testo dell'elemento dell'interfaccia utente per questo comando. Impostare il testo a un handle di stringa di testo.

## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxwinforms. h (definito nell'assembly atlmfc\lib\mfcmifc80.dll)  
  
## <a name="see-also"></a>Vedere anche  
 [Classe CCmdUI](../../mfc/reference/ccmdui-class.md)