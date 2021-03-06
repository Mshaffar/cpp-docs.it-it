---
title: Utilizzo di un elenco immagini con un controllo Rebar
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: fa5307c201850fc42439c79a1c638a0707379913
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180498"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Utilizzo di un elenco immagini con un controllo Rebar

Ogni controllo Rebar band può contenere, tra l'altro, un'immagine proveniente da un elenco di immagini associato. Nella procedura riportata di seguito vengono descritti in dettaglio i passaggi necessari per visualizzare un'immagine in un controllo Rebar band.

### <a name="to-display-images-in-a-rebar-band"></a>Per visualizzare le immagini in un Rebar band

1. Associare un elenco immagini all'oggetto controllo rebar effettuando una chiamata a [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), passando un puntatore a un elenco di immagini esistente.

1. Modificare il **REBARBANDINFO** struttura per assegnare un'immagine a un controllo rebar band:

   - Impostare il *fMask* membro `RBBIM_IMAGE`, usando l'operatore OR bit per bit per includere i flag aggiuntivi in base alle esigenze.

   - Impostare il *iImage* membro per l'indice dell'elenco immagini dell'immagine da visualizzare.

1. Inizializzare tutti i membri di dati restanti, ad esempio la dimensione, il testo e un handle della finestra figlio contenuta, con le informazioni necessarie.

1. Inserire il nuovo band (con l'immagine) con una chiamata a [CReBarCtrl:: InsertBand](../mfc/reference/crebarctrl-class.md#insertband), passando il **REBARBANDINFO** struttura.

Nell'esempio seguente si presuppone che un oggetto elenco immagini esistente con due immagini sia stato assegnato all'oggetto controllo Rebar (`m_wndReBar`). Un nuovo Rebar band (definito da `rbi`), che contiene la prima immagine, viene aggiunto tramite una chiamata a `InsertBand`:

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>Vedere anche

[Uso di CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controlli](../mfc/controls-mfc.md)
