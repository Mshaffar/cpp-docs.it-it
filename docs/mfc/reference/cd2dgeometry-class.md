---
title: Classe CD2DGeometry | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
dev_langs:
- C++
helpviewer_keywords:
- CD2DGeometry class
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
caps.latest.revision: 17
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 948b2e2154259557e3a52c2045586cffce2a16f8
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dgeometry-class"></a>Classe CD2DGeometry
Un wrapper per ID2D1Geometry.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CD2DGeometry : public CD2DResource;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Costruisce un oggetto CD2DGeometry.|  
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|Distruttore. Chiamato quando viene eliminato un oggetto geometry D2D.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DGeometry::Attach](#attach)|È possibile collegare interfaccia risorse per l'oggetto esistente|  
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Combina questa geometria con la geometria specificata e archivia il risultato in un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Descrive l'intersezione tra la geometria e la geometria specificata. Il confronto viene eseguito utilizzando la tolleranza bidimensionale specificata.|  
|[CD2DGeometry::ComputeArea](#computearea)|Viene calcolata l'area della geometria dopo che è stato trasformato dalla matrice specificata e bidimensionale utilizzando la tolleranza specificata.|  
|[CD2DGeometry::ComputeLength](#computelength)|Calcola la lunghezza della geometria come se ogni segmento fosse spiegato in una riga.|  
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Calcola il punto e il vettore tangente alla distanza specificata lungo la geometria dopo che è stato trasformato dalla matrice specificata e bidimensionale utilizzando la tolleranza specificata.|  
|[CD2DGeometry:: Destroy](#destroy)|Elimina un oggetto CD2DGeometry. (Esegue l'override di [CD2DResource:: Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DGeometry::Detach](#detach)|Disconnette l'interfaccia risorse dall'oggetto|  
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Indica se l'area riempita dalla geometria contiene il punto specificato base alla tolleranza bidimensionale specificata.|  
|[CD2DGeometry::Get](#get)|Restituisce l'interfaccia ID2D1Geometry|  
|[CD2DGeometry::GetBounds](#getbounds)||  
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Ottiene i limiti della geometria dopo che è stato esteso per la larghezza del tratto specificato e lo stile e trasformato dalla matrice specificata.|  
|[CD2DGeometry::IsValid](#isvalid)|Controlla la validità della risorsa (esegue l'override di [CD2DResource:: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DGeometry::Outline](#outline)|Calcola la struttura della geometria e scrive il risultato in un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::Simplify](#simplify)|Crea una versione semplificata della geometria che contiene solo linee e curve di Bézier cubiche (facoltativamente) e scrive il risultato in un ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Determina se il tratto della geometria contiene il punto specificato dato lo spessore del tratto specificato, stile e trasformazione.|  
|[CD2DGeometry::Tessellate](#tessellate)|Crea un set di in senso orario triangoli che analizzano la geometria dopo che è stata trasformata utilizzando la matrice specificata e bidimensionale utilizzando la tolleranza specificata.|  
|[CD2DGeometry::Widen](#widen)|Amplia la geometria in base al tratto specificato e scrive il risultato in un ID2D1SimplifiedGeometrySink dopo che è stato trasformato dalla matrice specificata e bidimensionale utilizzando la tolleranza specificata.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|Restituisce l'interfaccia ID2D1Geometry|  
  
### <a name="protected-data-members"></a>Membri dati protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Un puntatore a un ID2D1Geometry.|  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DGeometry`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxrendertarget. h  
  
##  <a name="_dtorcd2dgeometry"></a>CD2DGeometry:: ~ CD2DGeometry  
 Distruttore. Chiamato quando viene eliminato un oggetto geometry D2D.  
  
```  
virtual ~CD2DGeometry();
```  
  
##  <a name="attach"></a>CD2DGeometry::Attach  
 È possibile collegare interfaccia risorse per l'oggetto esistente  
  
```  
void Attach(ID2D1Geometry* pResource);
```  
  
### <a name="parameters"></a>Parametri  
 `pResource`  
 Interfaccia di risorse esistente. Non può essere NULL  
  
##  <a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry  
 Costruisce un oggetto CD2DGeometry.  
  
```  
CD2DGeometry(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametri  
 `pParentTarget`  
 Puntatore alla destinazione di rendering.  
  
 `bAutoDestroy`  
 Indica che l'oggetto verrà eliminata dal proprietario (pParentTarget).  
  
##  <a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry  
 Combina questa geometria con la geometria specificata e archivia il risultato in un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,  
    D2D1_COMBINE_MODE combineMode,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `inputGeometry`  
 La geometria da combinare con questa istanza.  
  
 `combineMode`  
 Il tipo di operazione di combinazione da eseguire.  
  
 `inputGeometryTransform`  
 La trasformazione da applicare a inputGeometry prima della combinazione.  
  
 `geometrySink`  
 Il risultato dell'operazione di combinazione.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale delle geometrie. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry  
 Descrive l'intersezione tra la geometria e la geometria specificata. Il confronto viene eseguito utilizzando la tolleranza bidimensionale specificata.  
  
```  
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,  
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `inputGeometry`  
 La geometria da testare.  
  
 `inputGeometryTransform`  
 La trasformazione da applicare a inputGeometry.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale delle geometrie. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="computearea"></a>CD2DGeometry::ComputeArea  
 Viene calcolata l'area della geometria dopo che è stato trasformato dalla matrice specificata e bidimensionale utilizzando la tolleranza specificata.  
  
```  
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& area,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `worldTransform`  
 La trasformazione da applicare a questa geometria prima di calcolare l'area.  
  
 `area`  
 Quando termina, questo metodo contiene un puntatore all'area della versione di questa geometria trasformata e bidimensionale. È necessario allocare spazio di archiviazione per questo parametro.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale della geometria. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="computelength"></a>CD2DGeometry::ComputeLength  
 Calcola la lunghezza della geometria come se ogni segmento fosse spiegato in una riga.  
  
```  
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    FLOAT& length,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `worldTransform`  
 La trasformazione da applicare alla geometria prima di calcolare la lunghezza.  
  
 `length`  
 Quando termina, questo metodo contiene un puntatore alla lunghezza della geometria. Per le geometrie chiuse, la lunghezza include un segmento di chiusura implicita. È necessario allocare spazio di archiviazione per questo parametro.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale della geometria. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength  
 Calcola il punto e il vettore tangente alla distanza specificata lungo la geometria dopo che è stato trasformato dalla matrice specificata e bidimensionale utilizzando la tolleranza specificata.  
  
```  
BOOL ComputePointAtLength(
    FLOAT length,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DPointF& point,  
    CD2DPointF& unitTangentVector,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `length`  
 La distanza lungo la geometria del punto e della tangente da trovare. Se la distanza è inferiore a 0, questo metodo calcola il primo punto di geometria. Se la distanza è maggiore della lunghezza della geometria, questo metodo calcola l'ultimo punto di geometria.  
  
 `worldTransform`  
 La trasformazione da applicare alla geometria prima di calcolare il punto specificato e una tangente.  
  
 `point`  
 Il percorso alla distanza lungo la geometria specificata. Se la geometria è vuota, questo punto contiene NaN come x e y valori.  
  
 `unitTangentVector`  
 Quando termina, questo metodo contiene un puntatore al vettore tangente alla distanza lungo la geometria specificata. Se la geometria è vuota, il vettore contiene NaN come x e y valori. È necessario allocare spazio di archiviazione per questo parametro.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale della geometria. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="destroy"></a>CD2DGeometry:: Destroy  
 Elimina un oggetto CD2DGeometry.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DGeometry::Detach  
 Disconnette l'interfaccia risorse dall'oggetto  
  
```  
ID2D1Geometry* Detach();
```  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a interfaccia risorse scollegato.  
  
##  <a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint  
 Indica se l'area riempita dalla geometria contiene il punto specificato base alla tolleranza bidimensionale specificata.  
  
```  
BOOL FillContainsPoint(
    CD2DPointF point,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `point`  
 Punto da verificare.  
  
 `worldTransform`  
 La trasformazione da applicare alla geometria prima di testare il contenimento.  
  
 `contains`  
 Quando termina, questo metodo contiene un valore booleano che è TRUE se l'area riempita dalla geometria contiene punto; in caso contrario, FALSE. È necessario allocare spazio di archiviazione per questo parametro.  
  
 `flatteningTolerance`  
 La precisione numerica con cui il percorso geometrico preciso e intersezione del percorso viene calcolato. Punti in cui Manca il riempimento per meno della tolleranza sono ancora considerati interni. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="get"></a>CD2DGeometry::Get  
 Restituisce l'interfaccia ID2D1Geometry  
  
```  
ID2D1Geometry* Get();
```  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a un'interfaccia ID2D1Geometry o NULL se l'oggetto non è ancora inizializzato.  
  
##  <a name="getbounds"></a>CD2DGeometry::GetBounds  
  
```   
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,  
CD2DRectF& bounds) const; 
```  
  
### <a name="parameters"></a>Parametri  
 `worldTransform`  
 `bounds`  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds  
 Ottiene i limiti della geometria dopo che è stato esteso per la larghezza del tratto specificato e lo stile e trasformato dalla matrice specificata.  
  
```  
BOOL GetWidenedBounds(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    CD2DRectF& bounds,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `strokeWidth`  
 La quantità da aumentare la geometria tratteggiando il contorno.  
  
 `strokeStyle`  
 Lo stile del tratto che amplia la geometria.  
  
 `worldTransform`  
 La trasformazione da applicare alla geometria dopo la geometria viene trasformata e dopo che è stata tracciata la geometria.  
  
 `bounds`  
 Quando questo metodo viene restituito, contiene i limiti della geometria ingrandita. È necessario allocare spazio di archiviazione per questo parametro.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale delle geometrie. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="isvalid"></a>CD2DGeometry::IsValid  
 Verifica la validità della risorsa  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 TRUE se la risorsa è valido. in caso contrario FALSE.  
  
##  <a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry  
 Un puntatore a un ID2D1Geometry.  
  
```  
ID2D1Geometry* m_pGeometry;  
```  
  
##  <a name="operator_id2d1geometry_star"></a>CD2DGeometry::operator ID2D1Geometry *  
 Restituisce l'interfaccia ID2D1Geometry  
  
```  
operator ID2D1Geometry*();
```   
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a un'interfaccia ID2D1Geometry o NULL se l'oggetto non è ancora inizializzato.  
  
##  <a name="outline"></a>CD2DGeometry::Outline  
 Calcola la struttura della geometria e scrive il risultato in un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `worldTransform`  
 La trasformazione da applicare alla struttura della geometria.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink a cui viene aggiunta la struttura di geometria trasformata.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale della geometria. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="simplify"></a>CD2DGeometry::Simplify  
 Crea una versione semplificata della geometria che contiene solo linee e curve di Bézier cubiche (facoltativamente) e scrive il risultato in un ID2D1SimplifiedGeometrySink.  
  
```  
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `simplificationOption`  
 Un valore che specifica se la geometria semplificata deve contenere curve.  
  
 `worldTransform`  
 La trasformazione da applicare alla geometria semplificata.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink a cui viene aggiunta la geometria semplificata.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale della geometria. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint  
 Determina se il tratto della geometria contiene il punto specificato dato lo spessore del tratto specificato, stile e trasformazione.  
  
```  
BOOL StrokeContainsPoint(
    CD2DPointF point,  
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    BOOL* contains,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `point`  
 Il punto di test di contenimento.  
  
 `strokeWidth`  
 Lo spessore del tratto da applicare.  
  
 `strokeStyle`  
 Stile del tratto da applicare.  
  
 `worldTransform`  
 La trasformazione da applicare alla geometria tratteggiata.  
  
 `contains`  
 Quando termina, questo metodo contiene un valore booleano impostato su TRUE se il tratto della geometria contiene il punto specificato; in caso contrario, FALSE. È necessario allocare spazio di archiviazione per questo parametro.  
  
 `flatteningTolerance`  
 La precisione numerica con cui il percorso geometrico preciso e intersezione del percorso viene calcolato. Punti in cui Manca il tratto da meno della tolleranza sono ancora considerati interni. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="tessellate"></a>CD2DGeometry::Tessellate  
 Crea un set di in senso orario triangoli che analizzano la geometria dopo che è stata trasformata utilizzando la matrice specificata e bidimensionale utilizzando la tolleranza specificata.  
  
```  
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1TessellationSink* tessellationSink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `worldTransform`  
 La trasformazione da applicare al geometria o NULL.  
  
 `tessellationSink`  
 ID2D1TessellationSink al quale viene aggiunto.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale della geometria. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
##  <a name="widen"></a>CD2DGeometry::Widen  
 Amplia la geometria in base al tratto specificato e scrive il risultato in un ID2D1SimplifiedGeometrySink dopo che è stato trasformato dalla matrice specificata e bidimensionale utilizzando la tolleranza specificata.  
  
```  
BOOL Widen(
    FLOAT strokeWidth,  
    ID2D1StrokeStyle* strokeStyle,  
    const D2D1_MATRIX_3X2_F& worldTransform,  
    ID2D1SimplifiedGeometrySink* geometrySink,  
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `strokeWidth`  
 La quantità da aumentare la geometria.  
  
 `strokeStyle`  
 Stile del tratto da applicare alla geometria, o NULL.  
  
 `worldTransform`  
 La trasformazione da applicare alla geometria dopo averla ingrandita.  
  
 `geometrySink`  
 ID2D1SimplifiedGeometrySink a cui viene aggiunta la geometria ampliata.  
  
 `flatteningTolerance`  
 Limiti massimi della distanza tra punti nell'approssimazione poligonale della geometria. I valori inferiori producono risultati più precisi, ma possono rallentare l'esecuzione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce TRUE. In caso contrario, restituisce FALSE.  
  
## <a name="see-also"></a>Vedere anche  
 [Classi](../../mfc/reference/mfc-classes.md)
