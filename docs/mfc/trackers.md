---
title: Tracker
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- OLE applications [MFC], trackers
- applications [OLE], trackers
- tracking OLE items [MFC]
- OLE containers [MFC], trackers
- CDC class [MFC], trackers
- CRectTracker class [MFC], implementing trackers
- OLE server applications [MFC], trackers
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
ms.openlocfilehash: b71eb0e5d46a790b01ec12f12043af783bdfcf27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181637"
---
# <a name="trackers"></a>Tracker

Il [CRectTracker](../mfc/reference/crecttracker-class.md) classe fornisce un'interfaccia utente tra gli elementi rettangolare nell'applicazione e l'utente fornendo un'ampia gamma di stili di visualizzazione. Questi stili di includono i bordi a tinta unita, tratteggiati o tratteggiati; un motivo a tratteggio che copre l'elemento; e quadratini di ridimensionamento che può essere archiviata all'esterno o all'interno di un bordo. Rilevazioni vengono spesso usati in combinazione con gli elementi OLE, vale a dire, gli oggetti derivati da `COleClientItem`. I rettangoli di tracker forniscono indicazioni visive sullo stato corrente dell'elemento.

L'esempio OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) illustra un'interfaccia comune usando strumenti per l'individuazione e gli elementi OLE client dal punto di vista di un'applicazione contenitore. Per una dimostrazione degli stili diversi e dalla capacità di un oggetto di individuazione, vedere l'esempio generale di MFC [TRACKER](../overview/visual-cpp-samples.md).

Per altre informazioni sull'implementazione di tracker nell'applicazione OLE, vedere [Tracker: implementazione di tracker nell'applicazione OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

## <a name="see-also"></a>Vedere anche

[OLE](../mfc/ole-in-mfc.md)<br/>
[Classe COleClientItem](../mfc/reference/coleclientitem-class.md)
