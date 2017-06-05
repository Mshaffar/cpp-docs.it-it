---
title: Classe CPoint | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 6b1afeea5a1d55fb3317b432871f2ed15dd5d19e
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cpoint-class"></a>Classe CPoint
Simile alla struttura `POINT` di Windows.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CPoint : public tagPOINT 
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CPoint::CPoint](#cpoint)|Costruisce un oggetto `CPoint`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CPoint::Offset](#offset)|Aggiunge i valori per il **x** e **y** i membri di `CPoint`.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CPoint::operator-](#operator_-)|Restituisce la differenza tra un `CPoint` e una dimensione o la negazione di un punto o la differenza tra due punti o l'offset in base alle dimensioni negative.|  
|[CPoint::operator! =](#operator_neq)|Verifica la disuguaglianza tra due punti.|  
|[CPoint::operator +](#operator_add)|Restituisce la somma di un `CPoint` e una dimensione o un punto o un `CRect` offset in base alle dimensioni.|  
|[+ = CPoint::operator](#operator_add_eq)|Offset `CPoint` mediante l'aggiunta di una dimensione o un punto.|  
|[CPoint::operator =](#operator_-_eq)|Offset `CPoint` sottraendo una dimensione o un punto.|  
|[CPoint::operator = =](#operator_eq_eq)|Verifica l'uguaglianza tra due punti.|  
  
## <a name="remarks"></a>Note  
 Contiene inoltre funzioni membro per manipolare `CPoint` e [punto](../../mfc/reference/point-structure1.md) strutture.  
  
 Oggetto `CPoint` oggetto può essere utilizzato ovunque un `POINT` struttura viene utilizzata. Gli operatori che interagiscono con una "dimensioni" di questa classe di accettare uno [CSize](../../atl-mfc-shared/reference/csize-class.md) oggetti o [dimensioni](http://msdn.microsoft.com/library/windows/desktop/dd145106) strutture, poiché i due sono intercambiabili.  
  
> [!NOTE]
>  Questa classe è derivata dal `tagPOINT` struttura. (Il nome `tagPOINT` è un nome meno utilizzato per il `POINT` struttura.) Ciò significa che i membri dei dati di `POINT` struttura, `x` e `y`, sono membri di dati accessibili di `CPoint`.  
  
> [!NOTE]
>  Per ulteriori informazioni su classi di utilità condivise (ad esempio `CPoint`), vedere [classi condivise](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `tagPOINT`  
  
 `CPoint`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** atltypes. h  
  
##  <a name="cpoint"></a>CPoint::CPoint
 Costruisce un oggetto `CPoint`.  
  
```  
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```  
  
### <a name="parameters"></a>Parametri  
 `initX`  
 Specificare il valore del membro `x` di `CPoint`.  
  
 `initY`  
 Specificare il valore del membro `y` di `CPoint`.  
  
 `initPt`  
 [PUNTO](../../mfc/reference/point-structure1.md) struttura o `CPoint` che specifica i valori utilizzati per inizializzare `CPoint`.  
  
 `initSize`  
 [DIMENSIONI](http://msdn.microsoft.com/library/windows/desktop/dd145106) struttura o [CSize](../../atl-mfc-shared/reference/csize-class.md) che specifica i valori utilizzati per inizializzare `CPoint`.  
  
 `dwPoint`  
 Impostare il membro `x` sulla parola word meno significativa di `dwPoint` e il membro `y` sulla parola più significativa di `dwPoint`.  
  
### <a name="remarks"></a>Note  
 Se non viene fornito alcun argomento, i membri `x` e `y` vengono impostate su 0.  
  
### <a name="example"></a>Esempio  
  
```cpp   
CPoint   ptTopLeft(0, 0); 
// works from a POINT, too  
 
POINT   ptHere;  
ptHere.x = 35;  
ptHere.y = 95;  
 
CPoint   ptMFCHere(ptHere);
 
// works from a SIZE 
SIZE   sHowBig;  
sHowBig.cx = 300;  
sHowBig.cy = 10;  
 
CPoint ptMFCBig(sHowBig); 
// or from a DWORD  
 
DWORD   dwSize;  
dwSize = MAKELONG(35, 95);
 
CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```  
  
##  <a name="offset"></a>CPoint::Offset  
 Aggiunge i valori per il **x** e **y** i membri di `CPoint`.  
  
```  
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```  
  
### <a name="parameters"></a>Parametri  
 *Sfalsamento x*  
 Specifica il valore di offset il **x** membro del `CPoint`.  
  
 *OffsetY*  
 Specifica il valore di offset il **y** membro del `CPoint`.  
  
 `point`  
 Specifica la quantità ( [punto](../../mfc/reference/point-structure1.md) o `CPoint`) per compensare la `CPoint`.  
  
 `size`  
 Specifica la quantità ( [dimensioni](http://msdn.microsoft.com/library/windows/desktop/dd145106) o [CSize](../../atl-mfc-shared/reference/csize-class.md)) per compensare la `CPoint`.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[28 NVC_ATLMFC_Utilities](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]  
  
##  <a name="operator_eq_eq"></a>CPoint::operator = =  
 Verifica l'uguaglianza tra due punti.  
  
```  
BOOL operator==(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parametri  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) struttura o `CPoint` oggetto.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se i punti sono uguali. in caso contrario 0.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATLMFC_Utilities&#29;](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]  
  
##  <a name="operator_neq"></a>CPoint::operator! =  
 Verifica la disuguaglianza tra due punti.  
  
```  
BOOL operator!=(POINT point) const throw();
```  
  
### <a name="parameters"></a>Parametri  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) struttura o `CPoint` oggetto.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se i punti non sono uguali. in caso contrario 0.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[&#30; NVC_ATLMFC_Utilities](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]  
  
##  <a name="operator_add_eq"></a>+ = CPoint::operator  
 Il primo overload aggiunge una dimensione per il `CPoint`.  
  
```  
void operator+=(SIZE size) throw(); 
void operator+=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parametri  
 `size`  
 Contiene un [dimensioni](http://msdn.microsoft.com/library/windows/desktop/dd145106) struttura o [CSize](../../atl-mfc-shared/reference/csize-class.md) oggetto.  
  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) struttura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) oggetto.  
  
### <a name="remarks"></a>Note  
 Il secondo overload viene aggiunto un punto per il `CPoint`.  
  
 In entrambi i casi, inoltre viene eseguita aggiungendo il **x** (o **cx**) membro dell'operando destro per il **x** membro del `CPoint` e aggiungendo il **y** (o **cy**) membro dell'operando destro per il **y** membro del `CPoint`.  
  
 Ad esempio, aggiungere `CPoint(5, -7)` a una variabile che contiene `CPoint(30, 40)` modifica la variabile `CPoint(35, 33)`.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATLMFC_Utilities&#31;](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]  
  
##  <a name="operator_-_eq"></a>CPoint::operator =  
 Il primo overload sottrae da una dimensione di `CPoint`.  
  
```  
void operator-=(SIZE size) throw(); 
void operator-=(POINT point) throw();
```  
  
### <a name="parameters"></a>Parametri  
 `size`  
 Contiene un [dimensioni](http://msdn.microsoft.com/library/windows/desktop/dd145106) struttura o [CSize](../../atl-mfc-shared/reference/csize-class.md) oggetto.  
  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) struttura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) oggetto.  
  
### <a name="remarks"></a>Note  
 Il secondo overload sottrae un punto di `CPoint`.  
  
 In entrambi i casi, la sottrazione viene eseguita sottraendo il **x** (o **cx**) membro dell'operando destro dal **x** membro del `CPoint` e sottraendo il **y** (o **cy**) membro dell'operando destro dal **y** membro del `CPoint`.  
  
 Ad esempio, la sottrazione `CPoint(5, -7)` da una variabile che contiene `CPoint(30, 40)` modifica la variabile `CPoint(25, 47)`.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATLMFC_Utilities n.&32;](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]  
  
##  <a name="operator_add"></a>CPoint::operator +  
 Utilizzare questo operatore per eseguire l'offset `CPoint` da un `CPoint` o `CSize` oggetto, o compensare un `CRect` da un `CPoint`.  
  
```  
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```  
  
### <a name="parameters"></a>Parametri  
 `size`  
 Contiene un [dimensioni](http://msdn.microsoft.com/library/windows/desktop/dd145106) struttura o [CSize](../../atl-mfc-shared/reference/csize-class.md) oggetto.  
  
 `point`  
 Contiene un [punto](../../mfc/reference/point-structure1.md) struttura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) oggetto.  
  
 `lpRect`  
 Contiene un puntatore a un [RECT](../../mfc/reference/rect-structure1.md) struttura o [CRect](../../atl-mfc-shared/reference/crect-class.md) oggetto.  
  
### <a name="return-value"></a>Valore restituito  
 Oggetto `CPoint` che offset in base a una dimensione, un **CPoint** che viene spostato da un punto o un **CRect** offset da un punto.  
  
### <a name="remarks"></a>Note  
 Ad esempio, utilizzando uno dei primi due overload per spostare il punto di `CPoint(25, -19)` da un punto di `CPoint(15, 5)` o dimensioni `CSize(15, 5)` restituisce il valore `CPoint(40, -14)`.  
  
 Aggiunta di un rettangolo a un punto restituisce il rettangolo dopo viene diminuito il **x** e **y** i valori specificati nel punto di. Ad esempio, utilizzando l'ultimo overload di offset di un rettangolo `CRect(125, 219, 325, 419)` da un punto di `CPoint(25, -19)` restituisce `CRect(150, 200, 350, 400)`.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATLMFC_Utilities n.&33;](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]  
  
##  <a name="operator_-"></a>CPoint::operator-  
 Utilizzare uno dei primi due overload per sottrarre un `CPoint` o `CSize` dell'oggetto da `CPoint`.  
  
```  
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```  
  
### <a name="parameters"></a>Parametri  
 `point`  
 Oggetto [punto](../../mfc/reference/point-structure1.md) struttura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) oggetto.  
  
 `size`  
 Oggetto [dimensioni](http://msdn.microsoft.com/library/windows/desktop/dd145106) struttura o [CSize](../../atl-mfc-shared/reference/csize-class.md) oggetto.  
  
 `lpRect`  
 Un puntatore a un [RECT](../../mfc/reference/rect-structure1.md) struttura o un [CRect](../../atl-mfc-shared/reference/crect-class.md) oggetto.  
  
### <a name="return-value"></a>Valore restituito  
 Un `CSize` che rappresenta la differenza tra due punti, un `CPoint` che è diminuito la negazione di una dimensione, un `CRect` che è diminuito la negazione di un punto o un `CPoint` vale a dire la negazione di un punto.  
  
### <a name="remarks"></a>Note  
 Il terzo overload offset un `CRect` per la negazione di `CPoint`. Infine, utilizzare l'operatore unario per negare `CPoint`.  
  
 Ad esempio, utilizzando il primo overload per calcolare la differenza tra due punti `CPoint(25, -19)` e `CPoint(15, 5)` restituisce `CSize(10, -24)`.  
  
 Sottrae un `CSize` da `CPoint` restituisce ma non lo stesso calcolo sopra un `CPoint` oggetto, non un `CSize` oggetto. Ad esempio, tramite il secondo overload per calcolare la differenza tra il punto `CPoint(25, -19)` e le dimensioni `CSize(15, 5)` restituisce `CPoint(10, -24)`.  
  
 Sottrazione di un rettangolo da un punto restituisce l'offset rettangolo da negativi del **x** e **y** i valori specificati nel punto di. Ad esempio, utilizzando l'ultimo overload per compensare il rettangolo `CRect(125, 200, 325, 400)` dal punto di `CPoint(25, -19)` restituisce `CRect(100, 219, 300, 419)`.  
  
 Utilizzare l'operatore unario per negare un punto. Ad esempio, utilizzando l'operatore unario con il punto di `CPoint(25, -19)` restituisce `CPoint(-25, 19)`.  
  
### <a name="example"></a>Esempio  
 [!code-cpp[NVC_ATLMFC_Utilities&#34;](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio MFC MDI](../../visual-cpp-samples.md)   
 [Grafico delle gerarchie](../../mfc/hierarchy-chart.md)   
 [Struttura POINT](../../mfc/reference/point-structure1.md)   
 [CRect (classe)](../../atl-mfc-shared/reference/crect-class.md)   
 [Classe CSize](../../atl-mfc-shared/reference/csize-class.md)



