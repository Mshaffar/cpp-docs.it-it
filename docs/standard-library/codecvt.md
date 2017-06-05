---
title: '&lt;codecvt&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- codecvt
- std::<codecvt>
- std.<codecvt>
- <codecvt>
dev_langs:
- C++
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 86978cd4549f0672dac7cad0e4713380ea189c27
ms.openlocfilehash: 75f527ca1e0742a1958076b49446b257793c69a5
ms.contentlocale: it-it
ms.lasthandoff: 04/18/2017

---
# <a name="ltcodecvtgt"></a>&lt;codecvt&gt;
Definisce diverse classi modello che descrivono oggetti basati sulla classe modello [codecvt](../standard-library/codecvt-class.md). Tali oggetti possono essere usati come [facet delle impostazioni locali](../standard-library/locale-class.md#facet_class) che controllano le conversioni tra una sequenza di valori di tipo `Elem` e una sequenza di valori di tipo `char`.  
  
## <a name="syntax"></a>Sintassi  
  
```  
#include <codecvt>  
  
```  
  
## <a name="remarks"></a>Note  
 I facet delle impostazioni locali dichiarati in questa intestazione eseguono la conversione tra diverse codifiche di caratteri. Per i caratteri wide (archiviati all'interno del programma come interi a dimensione fissa):  
  
-   UCS-4 è codificato con Unicode (ISO 10646) all'interno del programma  
  
-   UCS-4 è codificato con Unicode (ISO 10646) all'interno del programma come intero a 32 bit.  
  
-   UCS-2 è codificato con Unicode all'interno del programma  
  
-   UCS-2 è codificato con Unicode all'interno del programma come intero a 16 bit.  
  
-   UCS-16 è codificato con Unicode all'interno del programma come intero di uno dei due tipi.  
  
-   UCS-16 è codificato con Unicode all'interno del programma come uno dei due interi a 16 bit. Si noti che questo uso non soddisfa tutti i requisiti di una codifica di caratteri wide valida per C o C++ standard, ma è comunque ampiamente diffuso.  
  
 Per i flussi di byte (archiviati in un file, trasmessi come sequenza di byte o archiviati all'interno del programma in una matrice di `char`):  
  
-   UTF-8 è codificato con Unicode  
  
-   UTF-8 è codificato con Unicode all'interno di un flusso di byte come uno o più byte di otto bit con un ordine deterministico dei byte.  
  
-   UTF-16LE è codificato con Unicode  
  
-   UTF-16LE è codificato con Unicode in un flusso di byte come UTF-16 con ogni intero a 16 bit presentato come due byte di otto bit, con il byte meno significativo per primo.  
  
-   UTF-16BE è codificato con Unicode  
  
-   UTF-16BE è codificato con Unicode in un flusso di byte come UTF-16 con ogni intero a 16 bit presentato come due byte di otto bit, con il byte più significativo per primo.  
  
### <a name="enumerations"></a>Enumerazioni  
  
|||  
|-|-|  
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Specifica informazioni sulla configurazione per i facet delle impostazioni locali.|  
  
### <a name="classes"></a>Classi  
  
|||  
|-|-|  
|[codecvt_utf8](codecvt-utf8-class.md)|Rappresenta un facet di impostazioni locali che esegue la conversione tra caratteri wide codificati come UCS-2 o UCS-4 e un flusso di byte codificato come UTF-8.|  
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Rappresenta un facet di impostazioni locali che esegue la conversione tra caratteri wide codificati come UTF-16 e un flusso di byte codificato come UTF-8.|  
|[codecvt_utf16](codecvt-utf16-class.md)|Rappresenta un facet di impostazioni locali che esegue la conversione tra caratteri wide codificati come UCS-2 o UCS-4 e un flusso di byte codificato come UTF-16LE o UTF-16BE.|  

  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** \<codecvt>  
  
 **Spazio dei nomi:** stdt  
  
## <a name="see-also"></a>Vedere anche  
 [Header Files Reference](../standard-library/cpp-standard-library-header-files.md) (Riferimento file di intestazione)




