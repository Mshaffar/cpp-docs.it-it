---
title: Immagine informazioni negli elenchi di immagini | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33248c1bbc225d8d1ccf55c126d1657d0b0e4cad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="image-information-in-image-lists"></a>Informazioni sulle immagini negli elenchi di immagini
[CImageList](../mfc/reference/cimagelist-class.md) include una serie di funzioni che recuperano informazioni da un elenco di immagini. Il [funzione membro GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) funzione membro inserisce un `IMAGEINFO` struttura con informazioni su una singola immagine, inclusi gli handle di bitmap di immagine e mask, il numero di piani di colore e bit per pixel e il rettangolo di delimitazione dell'immagine all'interno della bitmap. È possibile utilizzare queste informazioni per modificare direttamente le bitmap per l'immagine.  
  
 Il [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount) membro funzione recupera il numero di immagini in un elenco di immagini.  
  
 È possibile creare un'icona basata su un'immagine e una maschera in un elenco di immagini tramite il [funzione membro ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) funzione membro. La funzione restituisce l'handle della nuova icona.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di CImageList](../mfc/using-cimagelist.md)   
 [Controlli](../mfc/controls-mfc.md)
