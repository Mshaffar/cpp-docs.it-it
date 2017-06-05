---
title: Istruzione for (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 20afe269d057d8ce856be1e1cccb32e6ca451c0f
ms.contentlocale: it-it
ms.lasthandoff: 04/04/2017

---
# <a name="for-statement-c"></a>Istruzione for (C)
L'istruzione **for** consente di ripetere un'istruzione o un'istruzione composta un numero specificato di volte. Il corpo di un'istruzione **for** viene eseguito zero o più volte fino a quando una condizione facoltativa non restituisce false. È possibile usare espressioni facoltative nell'istruzione **for** per inizializzare e modificare i valori durante l'esecuzione dell'istruzione **for**.  
  
## <a name="syntax"></a>Sintassi  
 *iteration-statement*:  
 &nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*  
  
 L'esecuzione di un'istruzione **for** procede nel modo seguente:  
  
1.  Se presente, viene valutato *init-expression*. Questo consente l'inizializzazione del ciclo. Non esistono restrizioni per il tipo di *init-expression*.  
  
2.  Se presente, viene valutato *cond-expression*. Questa espressione deve essere di tipo aritmetico o puntatore. Viene valutata prima di ogni iterazione. Sono possibili tre risultati:  
  
    -   Se *cond-expression* è **true** (diverso da zero), viene eseguito *statement*; quindi viene valutato *loop-expression*, se presente. *loop-expression* viene valutata al termine di ogni iterazione. Non esistono restrizioni per il relativo tipo. Gli effetti collaterali vengono eseguiti in ordine. Il processo inizia nuovamente con la valutazione di *cond-expression*.  
  
    -   Se *cond-expression* è omesso, *cond-expression* è considerato true e l'esecuzione prosegue esattamente come descritto nel paragrafo precedente. Un'istruzione **for** senza un argomento *cond-expression* termina solo quando viene eseguita un'istruzione **break** o **return** nel corpo dell'istruzione o quando viene eseguita un'istruzione **goto** (a un'istruzione con etichetta all'esterno del corpo dell'istruzione **for**).  
  
    -   Se *cond-expression* è **false** (0), l'esecuzione dell'istruzione **for** termina e il controllo passa all'istruzione successiva nel programma.  
  
 L'istruzione **for** può terminare anche quando un'istruzione **break**, **goto** o **return** viene eseguita nel corpo dell'istruzione. Un'istruzione **continue** in un ciclo **for** causa la valutazione di *loop-expression*. Quando un'istruzione **break** viene eseguita all'interno di un ciclo **for**, *loop-expression* non viene valutato né eseguito. Questa istruzione  
  
```  
for( ;; )  
```  
  
 è la modalità consueta di produrre un ciclo infinito che può essere terminato solo con un'istruzione **break**, **goto** o **return**.  
  
## <a name="code"></a>Codice  
 Questo esempio illustra l'istruzione **for**:  
  
```  
// c_for.c  
int main()  
{  
   char* line = "H e  \tl\tlo World\0";  
   int space = 0;  
   int tab = 0;  
   int i;  
   int max = strlen(line);  
   for (i = 0; i < max; i++ )   
   {  
      if ( line[i] == ' ' )  
      {  
          space++;  
      }  
      if ( line[i] == '\t' )  
      {  
          tab++;  
      }  
   }  
  
   printf("Number of spaces: %i\n", space);  
   printf("Number of tabs: %i\n", tab);  
   return 0;  
}  
```  
  
## <a name="output"></a>Output  
  
```  
Number of spaces: 4  
Number of tabs: 2  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni](../c-language/statements-c.md)