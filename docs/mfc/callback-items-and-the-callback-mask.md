---
title: Elementi di callback e maschera di callback
ms.date: 11/04/2016
helpviewer_keywords:
- callback items in CListCtrl class [MFC]
- CListCtrl class [MFC], callback item and callback mask
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
ms.openlocfilehash: 5c326d8498ea297936254a8650f666103ea3c772
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509140"
---
# <a name="callback-items-and-the-callback-mask"></a>Elementi di callback e maschera di callback

Per ogni elemento, un controllo visualizzazione elenco in genere archivia il testo dell'etichetta, l'indice dell'elenco di immagini delle icone dell'elemento e un set di flag di bit per lo stato dell'elemento. È possibile definire singoli elementi come elementi di callback, utili se l'applicazione archivia già alcune informazioni per un elemento.

Per definire un elemento come elemento di callback, è necessario specificare i valori `pszText` appropriati `iImage` per i membri `LVITEM` e della struttura (vedere [CListCtrl:: GetItem](../mfc/reference/clistctrl-class.md#getitem)). Se l'applicazione mantiene il testo dell'elemento o del sottoelemento, specificare il valore **LPSTR_TEXTCALLBACK** per il `pszText` membro. Se l'applicazione tiene traccia dell'icona per l'elemento, specificare il valore **I_IMAGECALLBACK** per il `iImage` membro.

Oltre a definire gli elementi di callback, è anche possibile modificare la maschera di callback del controllo. Questa maschera è un set di flag di bit che specificano gli Stati degli elementi per i quali l'applicazione, anziché il controllo, archivia i dati correnti. La maschera di callback viene applicata a tutti gli elementi del controllo, a differenza della designazione dell'elemento di callback che si applica a un elemento specifico. Per impostazione predefinita, la maschera di callback è zero, il che significa che il controllo tiene traccia di tutti gli Stati degli elementi. Per modificare questo comportamento predefinito, inizializzare la maschera su qualsiasi combinazione dei valori seguenti:

- **LVIS_CUT** L'elemento è contrassegnato per un'operazione di taglia e incolla.

- **LVIS_DROPHILITED** L'elemento è evidenziato come destinazione di trascinamento della selezione.

- **LVIS_FOCUSED** L'elemento ha lo stato attivo.

- **LVIS_SELECTED** L'elemento è selezionato.

- **LVIS_OVERLAYMASK** L'applicazione archivia l'indice dell'elenco immagini dell'immagine sovrapposta corrente per ogni elemento.

- **LVIS_STATEIMAGEMASK** L'applicazione archivia l'indice dell'elenco immagini dell'immagine di stato corrente per ogni elemento.

Per ulteriori informazioni sul recupero e l'impostazione di questa maschera, vedere [CListCtrl:: GetCallbackMask](../mfc/reference/clistctrl-class.md#getcallbackmask) e [CListCtrl:: SetCallbackMask](../mfc/reference/clistctrl-class.md#setcallbackmask).

## <a name="see-also"></a>Vedere anche

[Uso di CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controlli](../mfc/controls-mfc.md)
