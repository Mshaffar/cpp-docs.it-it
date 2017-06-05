---
title: "Costanti modalità di conversione | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
dev_langs:
- C++
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 2522ccf3c35a52141d3164bd2a35535a4068893e
ms.contentlocale: it-it
ms.lasthandoff: 04/01/2017

---
# <a name="translation-mode-constants"></a>Costanti modalità di conversione
## <a name="syntax"></a>Sintassi  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>Note  
 Le costanti di manifesto `_O_BINARY` e `_O_TEXT` determinano la modalità di conversione per i file (`_open` e `_sopen`) o la modalità di conversione per i flussi (`_setmode`).  
  
 Di seguito sono elencati i valori consentiti:  
  
 `_O_TEXT`  
 Apre un file in modalità testo (convertito). Le combinazioni di ritorno a capo - segno di avanzamento riga (CR-LF) sono convertite in un singolo carattere di avanzamento riga (LF) in fase di input. I caratteri di avanzamento riga sono convertiti in combinazioni di ritorno a capo -segno di avanzamento riga (CR-LF) in fase di output. Inoltre, CTRL+Z viene interpretato nell'input come carattere di fine file. Nei file aperti per la lettura e la lettura/scrittura, `fopen` verifica la presenza della combinazione CTRL+Z alla fine del file e la rimuove, se possibile. Questa operazione viene eseguita perché l'utilizzo delle funzioni `fseek` e `ftell` per spostarsi all'interno di un file che terminano con CTRL+Z può causare un comportamento non corretto di `fseek` in prossimità della fine del file.  
  
 `_O_BINARY`  
 Apre un file in modalità binaria (non convertita). Le conversioni precedenti vengono eliminate.  
  
 `_O_RAW`  
 Uguale a `_O_BINARY`. Supportata per la compatibilità con C 2.0.  
  
 Per altre informazioni, vedere [I/O file modalità testo e binaria](../c-runtime-library/text-and-binary-mode-file-i-o.md) e [Conversione di file](../c-runtime-library/file-translation-constants.md).  
  
## <a name="see-also"></a>Vedere anche  
 [_open, _wopen](../c-runtime-library/reference/open-wopen.md)   
 [_pipe](../c-runtime-library/reference/pipe.md)   
 [_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)   
 [_setmode](../c-runtime-library/reference/setmode.md)   
 [Costanti globali](../c-runtime-library/global-constants.md)