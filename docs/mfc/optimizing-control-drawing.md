---
title: Ottimizzazione del disegno dei controlli
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 354ec1678747be57d387673f2611d526df8dfb47
ms.sourcegitcommit: 0ad35b26e405bbde17dc0bd0141e72f78f0a38fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/18/2019
ms.locfileid: "67194728"
---
# <a name="optimizing-control-drawing"></a>Ottimizzazione del disegno dei controlli

Quando viene richiesto a un controllo di disegnarsi in un contesto di dispositivo fornito dal contenitore, il controllo in genere seleziona gli oggetti GDI (come penne, pennelli e tipi di carattere) nel contesto di dispositivo, esegue le operazioni di disegno e ripristina gli oggetti GDI precedenti. Se il contenitore ha più controlli che devono essere disegnati nello stesso contesto di dispositivo e ogni controllo seleziona gli oggetti GDI necessari, è possibile risparmiare tempo se i controlli non ripristinano individualmente gli oggetti precedentemente selezionati. Una volta che tutti i controlli sono stati disegnati, il contenitore può automaticamente ripristinare gli oggetti originali.

Per rilevare se un contenitore supporta questa tecnica, è possibile chiamare un controllo con il [COleControl:: IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) funzione membro. Se questa funzione restituisce **TRUE**, il controllo può ignorare il passaggio di ripristino degli oggetti precedentemente selezionati.

Si consideri un controllo con la seguente funzione `OnDraw` (non ottimizzata):

[!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]

La penna e il pennello in questo esempio sono variabili locali e pertanto i relativi distruttori verranno chiamati quando escono dall'ambito (quando termina la funzione `OnDraw`). I distruttori cercheranno di eliminare gli oggetti GDI corrispondenti. Ma non devono essere eliminati se si intende lasciarli selezionati nel contesto di dispositivo restituito da `OnDraw`.

Per evitare il [CPen](../mfc/reference/cpen-class.md) e [CBrush](../mfc/reference/cbrush-class.md) oggetti vengano eliminati definitivamente quando `OnDraw` al termine, archiviarli in variabili membro anziché le variabili locali. Nella dichiarazione della classe del controllo, aggiungere le dichiarazioni per due nuove variabili membro:

[!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]

È quindi possibile riscrivere la funzione `OnDraw` come segue:

[!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]

In questo modo si evita la creazione della penna e del pennello ogni volta che viene chiamata la funzione `OnDraw`. Il miglioramento nella velocità avviene a costo di mantenere dati aggiuntivi dell'istanza.

Se la proprietà ForeColor o BackColor cambia, la penna o il pennello devono essere ricreati. A tale scopo, eseguire l'override di [OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) e [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) funzioni membro:

[!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Infine, eliminare le chiamate di `SelectObject` non necessarie e modificare `OnDraw` come segue:

[!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Vedere anche

[Controlli ActiveX MFC: ottimizzazione](../mfc/mfc-activex-controls-optimization.md)<br/>
[Classe COleControl](../mfc/reference/colecontrol-class.md)<br/>
[Controlli ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Creazione guidata controllo ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Controlli ActiveX MFC: disegno di un controllo ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)
