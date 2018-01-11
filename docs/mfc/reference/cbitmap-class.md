---
title: CBitmap (classe) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs: C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33e0ca4c92d22d8afaed4523a7f274b6b5d20a2b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/24/2017
---
# <a name="cbitmap-class"></a>CBitmap (classe)
Incapsula una bitmap GDI (Graphics Device Interface) di Windows e fornisce funzioni membro per la modifica della bitmap.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|Costruisce un oggetto `CBitmap`.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|Inizializza l'oggetto con una bitmap in memoria dipendente dal dispositivo che dispone di una larghezza, altezza e schema di bit.|  
|[CBitmap:: Createbitmapindirect](#createbitmapindirect)|Inizializza l'oggetto con una bitmap con la larghezza, altezza e schema di bit (se ne è specificata) fornito un **BITMAP** struttura.|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Inizializza l'oggetto con una bitmap in modo che sia compatibile con un dispositivo specifico.|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Inizializza l'oggetto con una bitmap scaricabile che è compatibile con un dispositivo specifico.|  
|[CBitmap::FromHandle](#fromhandle)|Restituisce un puntatore a un `CBitmap` oggetto quando viene specificato un handle a un Windows `HBITMAP` bitmap.|  
|[CBitmap::GetBitmap](#getbitmap)|Riempie una **BITMAP** struttura con le informazioni della bitmap.|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|Copia i bit della bitmap specificata nel buffer specificato.|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Restituisce la larghezza e altezza della bitmap. L'altezza e larghezza si presuppone che siano già state configurate il [SetBitmapDimension](#setbitmapdimension) funzione membro.|  
|[LoadBitmap](#loadbitmap)|Inizializza l'oggetto durante il caricamento di una risorsa bitmap denominata dal file eseguibile dell'applicazione e connettendo la bitmap per l'oggetto.|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Carica un'immagine bitmap e mappe di colori per i colori di sistema corrente.|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Inizializza l'oggetto durante il caricamento di una bitmap di Windows predefinita e connettendo la bitmap per l'oggetto.|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|Imposta i bit di una bitmap per i valori di bit specificato.|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Assegna una larghezza e altezza di una bitmap in unità 0,1 millimetri.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[HBITMAP CBitmap::operator](#operator_hbitmap)|Restituisce l'handle di Windows collegata la `CBitmap` oggetto.|  
  
## <a name="remarks"></a>Note  
 Per utilizzare un `CBitmap` dell'oggetto, costruire l'oggetto, associare un handle di bitmap con uno delle funzioni membro di inizializzazione e quindi chiamare le funzioni membro dell'oggetto.  
  
 Per ulteriori informazioni sull'utilizzo di oggetti grafici come `CBitmap`, vedere [oggetti grafico](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxwin.h  
  
##  <a name="cbitmap"></a>CBitmap::CBitmap  
 Costruisce un oggetto `CBitmap`.  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>Note  
 L'oggetto risultante deve essere inizializzata con una delle funzioni membro di inizializzazione.  
  
##  <a name="createbitmap"></a>CBitmap::CreateBitmap  
 Inizializza una bitmap in memoria dipendente dal dispositivo che presenta la larghezza, l'altezza e lo schema di bit specificati.  
  
```  
BOOL CreateBitmap(
    int nWidth,  
    int nHeight,  
    UINT nPlanes,  
    UINT nBitcount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parametri  
 `nWidth`  
 Specifica la larghezza della bitmap (in pixel).  
  
 `nHeight`  
 Specifica l'altezza della bitmap (in pixel).  
  
 `nPlanes`  
 Specifica il numero dei piani di colore nella bitmap.  
  
 `nBitcount`  
 Specifica il numero di bit di colore per pixel visualizzato.  
  
 `lpBits`  
 Punta a una matrice di byte che contiene i valori iniziali dei bit della bitmap. Se è **NULL**, la nuova bitmap rimane non inizializzata.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Per una bitmap a colori, il parametro `nPlanes` o `nBitcount` deve essere impostato su 1. Se entrambi i parametri vengono impostati su 1, `CreateBitmap` crea una bitmap monocromatica.  
  
 Anche se non è possibile selezionare direttamente una bitmap per un dispositivo di visualizzazione, può essere selezionato come bitmap corrente per un "contesto di dispositivo memoria" usando [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) e copiato per qualsiasi contesto di dispositivo compatibili con la [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) (funzione).  
  
 Terminate le operazioni sull'oggetto `CBitmap` creato dalla funzione `CreateBitmap` , selezionare la bitmap dal contesto di memoria, quindi eliminare l'oggetto `CBitmap` .  
  
 Per altre informazioni, vedere la descrizione del campo **bmBits** nella struttura **BITMAP** . Il [BITMAP](../../mfc/reference/bitmap-structure.md) struttura è descritta sotto il [CBitmap:: Createbitmapindirect](#createbitmapindirect) funzione membro.  
  
##  <a name="createbitmapindirect"></a>CBitmap:: Createbitmapindirect  
 Inizializza una bitmap che presenta la larghezza, altezza e schema di bit (se ne è specificata) specificato nella struttura a cui puntava `lpBitmap`.  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>Parametri  
 `lpBitmap`  
 Punta a un [BITMAP](../../mfc/reference/bitmap-structure.md) struttura che contiene informazioni sulle bitmap.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Anche se non è possibile selezionare direttamente una bitmap per un dispositivo di visualizzazione, potrà essere selezionato come bitmap corrente per un contesto di dispositivo di memoria tramite [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) e copiato per qualsiasi contesto di dispositivo compatibili con la [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) o [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) (funzione). (Il [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt) funzione possibile copiare la bitmap per il pennello corrente direttamente nel contesto di dispositivo di visualizzazione.)  
  
 Se il **BITMAP** struttura a cui punta il `lpBitmap` parametro è stato compilato utilizzando il `GetObject` funzione, i bit della bitmap non vengono specificati e la bitmap non è inizializzata. Per inizializzare la bitmap, un'applicazione può utilizzare una funzione, ad esempio [CDC:: BitBlt](../../mfc/reference/cdc-class.md#bitblt) o [SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973) per copiare i bit della bitmap identificata dal parametro prima di `CGdiObject::GetObject` nella bitmap creato da `CreateBitmapIndirect`.  
  
 Una volta terminato con il `CBitmap` oggetto creato con `CreateBitmapIndirect` funzione, selezionare innanzitutto la bitmap dal contesto di dispositivo, quindi eliminare il `CBitmap` oggetto.  
  
##  <a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap  
 Inizializza una bitmap compatibile con il dispositivo specificato dal `pDC`.  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametri  
 `pDC`  
 Specifica il contesto di dispositivo.  
  
 `nWidth`  
 Specifica la larghezza della bitmap (in pixel).  
  
 `nHeight`  
 Specifica l'altezza della bitmap (in pixel).  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 La bitmap non ha lo stesso numero di piani di colore o lo stesso formato di bit per pixel del contesto di dispositivo specificato. È possibile selezionare come bitmap corrente per tutte le periferiche di memoria che sono compatibile con quello specificato da `pDC`.  
  
 Se `pDC` è un contesto di dispositivo di memoria, la bitmap restituita non ha lo stesso formato di bitmap attualmente selezionato in tale contesto di dispositivo. Un "contesto di dispositivo memoria" è un blocco di memoria che rappresenta una superficie di visualizzazione. E può essere utilizzato per preparare immagini in memoria prima di copiarli all'area di visualizzazione effettivo del dispositivo compatibile.  
  
 Quando viene creato un contesto di dispositivo di memoria, GDI seleziona automaticamente una bitmap monocromatica di azioni per tale.  
  
 Poiché un contesto di dispositivo colore memoria può avere colore o Bitmap monocromatica selezionata, il formato della bitmap restituito dal `CreateCompatibleBitmap` funzione non è sempre lo stesso, tuttavia, il formato di una bitmap compatibile per un contesto di dispositivo nonmemory è sempre nel formato del dispositivo.  
  
 Una volta terminato con il `CBitmap` oggetto creato con il `CreateCompatibleBitmap` funzione, selezionare innanzitutto la bitmap dal contesto di dispositivo, quindi eliminare il `CBitmap` oggetto.  
  
##  <a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap  
 Inizializza una bitmap scaricabile che è compatibile con il contesto di dispositivo identificato da `pDC`.  
  
```  
BOOL CreateDiscardableBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametri  
 `pDC`  
 Specifica un contesto di dispositivo.  
  
 `nWidth`  
 Specifica la larghezza della bitmap (in bit).  
  
 `nHeight`  
 Specifica l'altezza della bitmap (in bit).  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 La bitmap non ha lo stesso numero di piani di colore o lo stesso formato di bit per pixel del contesto di dispositivo specificato. Un'applicazione è possibile selezionare questa bitmap come bitmap corrente per un dispositivo di memoria che è compatibile con quello specificato da `pDC`.  
  
 Windows è possibile rimuovere una bitmap creata da questa funzione solo se un'applicazione non è stato selezionato in un contesto di visualizzazione. Se Windows elimina la bitmap quando non è selezionata e in un secondo momento l'applicazione tenta di selezionare il [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) funzione restituirà **NULL**.  
  
 Una volta terminato con il `CBitmap` oggetto creato con il `CreateDiscardableBitmap` funzione, selezionare innanzitutto la bitmap dal contesto di dispositivo, quindi eliminare il `CBitmap` oggetto.  
  
##  <a name="fromhandle"></a>CBitmap::FromHandle  
 Restituisce un puntatore a un `CBitmap` oggetto quando viene specificato un handle per una bitmap GDI di Windows.  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parametri  
 `hBitmap`  
 Specifica una bitmap GDI di Windows.  
  
### <a name="return-value"></a>Valore restituito  
 Un puntatore a un `CBitmap` oggetto in caso di esito positivo; in caso contrario **NULL**.  
  
### <a name="remarks"></a>Note  
 Se un `CBitmap` oggetto non è già collegato all'handle di una password temporanea `CBitmap` oggetto viene creato e collegato. Questo temporaneo `CBitmap` oggetto è valido solo finché la volta successiva che l'applicazione è il tempo di inattività nel relativo ciclo di eventi, che ora immagine temporanea tutti gli oggetti vengono eliminati. In altre parole, questo è che l'oggetto temporaneo è valido solo durante l'elaborazione di una finestra di messaggio.  
  
##  <a name="getbitmap"></a>CBitmap::GetBitmap  
 Recupera le proprietà dell'immagine per la bitmap associata.  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>Parametri  
 `pBitMap`  
 Puntatore a un [struttura BITMAP](../../mfc/reference/bitmap-structure.md) struttura che riceverà le proprietà dell'immagine. Questo parametro non deve essere `NULL`.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se il metodo ha esito positivo. in caso contrario 0.  
  
### <a name="remarks"></a>Note  
  
##  <a name="getbitmapbits"></a>CBitmap::GetBitmapBits  
 Copia lo schema di bit della bitmap associata nel buffer specificato.  
  
```  
DWORD GetBitmapBits(
    DWORD dwCount,  
    LPVOID lpBits) const;  
```  
  
### <a name="parameters"></a>Parametri  
 `dwCount`  
 Numero di byte da copiare nel buffer.  
  
 `lpBits`  
 Puntatore al buffer che riceverà la bitmap.  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di byte copiati nel buffer se il metodo ha esito positivo. in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Utilizzare [CBitmap::GetBitmap](#getbitmap) per determinare le dimensioni del buffer richiesto.  
  
##  <a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension  
 Restituisce la larghezza e altezza della bitmap.  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 La larghezza e altezza della bitmap, misurato in unità 0,1 millimetri. L'altezza è nel **cy** membro del `CSize` è oggetto e la larghezza di **cx** membro. Se la larghezza della bitmap e l'altezza non sono state impostate tramite `SetBitmapDimension`, il valore restituito è 0.  
  
### <a name="remarks"></a>Note  
 L'altezza e larghezza si presuppone che siano già state configurate utilizzando il [SetBitmapDimension](#setbitmapdimension) funzione membro.  
  
##  <a name="loadbitmap"></a>LoadBitmap  
 Carica la risorsa bitmap denominata da `lpszResourceName` o identificati dal numero di ID nella `nIDResource` dal file eseguibile dell'applicazione.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametri  
 `lpszResourceName`  
 Punta a una stringa con terminazione null che contiene il nome della risorsa bitmap.  
  
 `nIDResource`  
 Specifica il numero di ID risorsa della risorsa bitmap.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Bitmap caricata è collegata la `CBitmap` oggetto.  
  
 Se la bitmap è identificato da `lpszResourceName` non esiste o se è presente memoria insufficiente per caricare la mappa di bit, la funzione restituisce 0.  
  
 È possibile utilizzare il [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) funzione eliminare bitmap caricata dal `LoadBitmap` funzione, o `CBitmap` distruttore eliminerà automaticamente l'oggetto.  
  
> [!CAUTION]
>  Prima di eliminare l'oggetto, assicurarsi che non è selezionata in un contesto di dispositivo.  
  
 Le bitmap seguenti sono state aggiunte alle versioni di Windows 3.1 e versioni successive:  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 Queste bitmap non disponibili nel driver di dispositivo per le versioni di Windows 3.0 e versioni precedenti. Per un elenco completo di bitmap e una visualizzazione dell'aspetto, vedi il Windows SDK.  
  
##  <a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap  
 Chiamare questa funzione membro per caricare una bitmap ed eseguire il mapping dei colori per i colori di sistema corrente.  
  
```  
BOOL LoadMappedBitmap(
    UINT nIDBitmap,  
    UINT nFlags = 0,  
    LPCOLORMAP lpColorMap = NULL,  
    int nMapSize = 0);
```  
  
### <a name="parameters"></a>Parametri  
 `nIDBitmap`  
 L'ID della risorsa bitmap.  
  
 `nFlags`  
 Flag per una bitmap. Può essere zero o **CMB_MASKED**.  
  
 `lpColorMap`  
 Un puntatore a un **COLORMAP** struttura che contiene le informazioni di colore necessarie per eseguire il mapping di bitmap. Se questo parametro è **NULL**, la funzione utilizza la mappa di colori predefinita.  
  
 *nMapSize*  
 Il numero di mappe a colori a cui puntava `lpColorMap`.  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Per impostazione predefinita, `LoadMappedBitmap` i colori utilizzati nei glifi pulsante verrà eseguito il mapping.  
  
 Per informazioni sulla creazione di una bitmap con mapping, vedere la funzione Windows [CreateMappedBitmap](http://go.microsoft.com/fwlink/linkid=230562) e [COLORMAP](http://msdn.microsoft.com/library/windows/desktop/bb760448) struttura in Windows SDK.  
  
##  <a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap  
 Carica una bitmap predefinita utilizzata da Windows.  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>Parametri  
 `nIDBitmap`  
 Numero di ID della bitmap di Windows predefinite. I valori possibili sono elencati di seguito da WINDOWS. H:  
  
|||  
|-|-|  
|**OBM_BTNCORNERS**|**OBM_OLD_RESTORE**|  
|**OBM_BTSIZE**|**OBM_OLD_RGARROW**|  
|**OBM_CHECK**|**OBM_OLD_UPARROW**|  
|**OBM_CHECKBOXES**|**OBM_OLD_ZOOM**|  
|**OBM_CLOSE**|**OBM_REDUCE**|  
|**OBM_COMBO**|**OBM_REDUCED**|  
|**OBM_DNARROW**|**OBM_RESTORE**|  
|**OBM_DNARROWD**|**OBM_RESTORED**|  
|**OBM_DNARROWI**|**OBM_RGARROW**|  
|**OBM_LFARROW**|**OBM_RGARROWD**|  
|**OBM_LFARROWD**|**OBM_RGARROWI**|  
|**OBM_LFARROWI**|**OBM_SIZE**|  
|**OBM_MNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_CLOSE**|**OBM_UPARROWD**|  
|**OBM_OLD_DNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_LFARROW**|**OBM_ZOOM**|  
|**OBM_OLD_REDUCE**|**OBM_ZOOMD**|  
  
### <a name="return-value"></a>Valore restituito  
 Diverso da zero se ha esito positivo; in caso contrario 0.  
  
### <a name="remarks"></a>Note  
 Bitmap di nomi che iniziano con **OBM_OLD** rappresentano bitmap usata dalle versioni di Windows precedente alla 3.0.  
  
 Si noti che la costante **OEMRESOURCE** deve essere definita prima tra cui WINDOWS. H per usare il **OBM_** costanti.  
  
##  <a name="operator_hbitmap"></a>HBITMAP CBitmap::operator  
 Utilizzare questo operatore per ottenere l'handle GDI di Windows associata del `CBitmap` oggetto.  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, un handle all'oggetto GDI di Windows rappresentato dal `CBitmap` oggetto; in caso contrario **NULL**.  
  
### <a name="remarks"></a>Note  
 Questo è un operatore di cast, che supporta l'utilizzo diretto di un `HBITMAP` oggetto.  
  
 Per ulteriori informazioni sull'utilizzo di oggetti grafici, vedere [oggetti immagine di](http://msdn.microsoft.com/library/windows/desktop/dd144962) in Windows SDK.  
  
##  <a name="setbitmapbits"></a>CBitmap::SetBitmapBits  
 Imposta i bit di una bitmap per i valori di bit specificati da `lpBits`.  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>Parametri  
 `dwCount`  
 Specifica il numero di byte a cui puntata `lpBits`.  
  
 `lpBits`  
 Punta al **BYTE** matrice che contiene i valori pixel per copiare il `CBitmap` oggetto. Per la bitmap essere in grado di eseguire il rendering immagine correttamente, i valori devono essere formattati per essere conformi ai valori di profondità di altezza, larghezza e il colore che sono stati specificati quando è stata creata l'istanza di CBitmap. Per ulteriori informazioni, vedere [CBitmap::CreateBitmap](#createbitmap).  
  
### <a name="return-value"></a>Valore restituito  
 Il numero di byte utilizzati nel impostando i bit della bitmap; 0 se la funzione ha esito negativo.  
  
##  <a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension  
 Assegna una larghezza e altezza di una bitmap in unità 0,1 millimetri.  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parametri  
 `nWidth`  
 Specifica la larghezza della bitmap (in unità 0,1 millimetro).  
  
 `nHeight`  
 Specifica l'altezza della bitmap (in unità 0,1 millimetro).  
  
### <a name="return-value"></a>Valore restituito  
 Le dimensioni di bitmap precedente. Altezza è nel **cy** variabile membro del `CSize` oggetto e la larghezza è il **cx** variabile membro.  
  
### <a name="remarks"></a>Note  
 GDI non usa questi valori, ad eccezione di to restituirle quando un'applicazione chiama il [GetBitmapDimension](#getbitmapdimension) funzione membro.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio MFC MDI](../../visual-cpp-samples.md)   
 [Classe CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Grafico della gerarchia](../../mfc/hierarchy-chart.md)
