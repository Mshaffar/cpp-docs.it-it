---
title: Classe CD2DBitmap | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
dev_langs:
- C++
helpviewer_keywords:
- CD2DBitmap class
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
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
ms.openlocfilehash: f88a6376069c07c61311d74faca104e821a259bd
ms.contentlocale: it-it
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dbitmap-class"></a>Classe CD2DBitmap
Un wrapper per ID2D1Bitmap.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CD2DBitmap : public CD2DResource;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Di overload. Costruisce un oggetto CD2DBitmap da HBITMAP.|  
|[CD2DBitmap:: ~ CD2DBitmap](#_dtorcd2dbitmap)|Distruttore. Chiamato quando viene eliminato un oggetto bitmap D2D.|  
  
### <a name="protected-constructors"></a>Costruttori protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Di overload. Costruisce un oggetto CD2DBitmap.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DBitmap::Attach](#attach)|È possibile collegare interfaccia risorse per l'oggetto esistente|  
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Copia nell'area specificata da nella bitmap specificata nella bitmap corrente|  
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Copia la regione specificata dalla memoria nella bitmap corrente|  
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Copia nell'area specificata dall'oggetto specificato destinazione rendering nella bitmap corrente|  
|[CD2DBitmap::Create](#create)|Crea un CD2DBitmap. (Esegue l'override di [CD2DResource:: Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DBitmap::Destroy](#destroy)|Elimina un oggetto CD2DBitmap. (Esegue l'override di [CD2DResource:: Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DBitmap::Detach](#detach)|Disconnette l'interfaccia risorse dall'oggetto|  
|[CD2DBitmap::Get](#get)|Restituisce l'interfaccia ID2D1Bitmap|  
|[CD2DBitmap::GetDPI](#getdpi)|Restituire i punti per pollice (DPI) della bitmap|  
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Recupera la modalità di alfa e formato pixel della bitmap|  
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Restituisce la dimensione, in unità dipendenti dalla periferica (pixel), dell'immagine bitmap|  
|[CD2DBitmap::GetSize](#getsize)|Restituisce la dimensione, in pixel indipendenti dal dispositivo (DIP), dell'immagine bitmap|  
|[CD2DBitmap::IsValid](#isvalid)|Controlla la validità della risorsa (esegue l'override di [CD2DResource:: IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
  
### <a name="protected-methods"></a>Metodi protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DBitmap::CommonInit](#commoninit)|Inizializza l'oggetto|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DBitmap::operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Restituisce l'interfaccia ID2D1Bitmap|  
  
### <a name="protected-data-members"></a>Membri dati protetti  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUE se m_hBmpSrc deve essere eliminato; in caso contrario FALSE.|  
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Handle di bitmap di origine.|  
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Tipo di risorsa.|  
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Archivia un puntatore a un oggetto ID2D1Bitmap.|  
|[CD2DBitmap::m_sizeDest](#m_sizedest)|Dimensione di destinazione bitmap.|  
|[CD2DBitmap::m_strPath](#m_strpath)|Del file botmap.|  
|[CD2DBitmap::m_uiResID](#m_uiresid)|ID della risorsa bitmap|  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DBitmap`
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxrendertarget. h  
  
##  <a name="_dtorcd2dbitmap"></a>CD2DBitmap:: ~ CD2DBitmap  
 Distruttore. Chiamato quando viene eliminato un oggetto bitmap D2D.  
  
```  
virtual ~CD2DBitmap();
```  
  
##  <a name="attach"></a>CD2DBitmap::Attach  
 È possibile collegare interfaccia risorse per l'oggetto esistente  
  
```  
void Attach(ID2D1Bitmap* pResource);
```  
  
### <a name="parameters"></a>Parametri  
 `pResource`  
 Interfaccia di risorse esistente. Non può essere NULL  
  
##  <a name="cd2dbitmap"></a>CD2DBitmap::CD2DBitmap  
 Costruisce un oggetto CD2DBitmap dalla risorsa.  
  
```  
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    UINT uiResID,  
    LPCTSTR lpszType = NULL,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    LPCTSTR lpszPath,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    HBITMAP hbmpSrc,  
    CD2DSizeU sizeDest = CD2DSizeU(0, 0), 
    BOOL bAutoDestroy = TRUE);

 
CD2DBitmap(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametri  
 `pParentTarget`  
 Puntatore alla destinazione di rendering.  
  
 `uiResID`  
 Il numero di ID risorsa della risorsa.  
  
 `lpszType`  
 Puntatore a una stringa con terminazione null che contiene il tipo di risorsa.  
  
 `sizeDest`  
 Dimensione di destinazione della bitmap.  
  
 `bAutoDestroy`  
 Indica che l'oggetto verrà eliminata dal proprietario (pParentTarget).  
  
 `lpszPath`  
 Puntatore a una stringa con terminazione null che contiene il nome del file.  
  
 `hbmpSrc`  
 Handle per la bitmap.  
  
##  <a name="commoninit"></a>CD2DBitmap::CommonInit  
 Inizializza l'oggetto  
  
```  
void CommonInit();
```  
  
##  <a name="copyfrombitmap"></a>CD2DBitmap::CopyFromBitmap  
 Copia nell'area specificata da nella bitmap specificata nella bitmap corrente  
  
```  
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parametri  
 `pBitmap`  
 La bitmap di origine  
  
 `destPoint`  
 Nella bitmap corrente, viene copiato nell'angolo superiore sinistro dell'area a cui l'area specificata da srcRect  
  
 `srcRect`  
 L'area dell'immagine bitmap da copiare  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. In caso contrario, restituisce un codice di errore HRESULT.  
  
##  <a name="copyfrommemory"></a>CD2DBitmap::CopyFromMemory  
 Copia la regione specificata dalla memoria nella bitmap corrente  
  
```  
HRESULT CopyFromMemory(
    const void* srcData,  
    UINT32 pitch,  
    const CD2DRectU* destRect = NULL);
```  
  
### <a name="parameters"></a>Parametri  
 `srcData`  
 I dati da copiare  
  
 `pitch`  
 Lo stride o passo, la bitmap di origine archiviate in srcData. Stride è il numero di byte di una linea di digitalizzazione (una riga di pixel in memoria). Lo stride può essere calcolato dalla formula seguente: larghezza in pixel * byte per pixel + riempimento della memoria  
  
 `destRect`  
 Nella bitmap corrente, viene copiato nell'angolo superiore sinistro dell'area a cui l'area specificata da srcRect  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. In caso contrario, restituisce un codice di errore HRESULT.  
  
##  <a name="copyfromrendertarget"></a>CD2DBitmap::CopyFromRenderTarget  
 Copia nell'area specificata dall'oggetto specificato destinazione rendering nella bitmap corrente  
  
```  
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,  
    const CD2DPointU* destPoint = NULL,  
    const CD2DRectU* srcRect = NULL);
```  
  
### <a name="parameters"></a>Parametri  
 `pRenderTarget`  
 La destinazione di rendering che contiene l'area da copiare  
  
 `destPoint`  
 Nella bitmap corrente, viene copiato nell'angolo superiore sinistro dell'area a cui l'area specificata da srcRect  
  
 `srcRect`  
 L'area di renderTarget da copiare  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. In caso contrario, restituisce un codice di errore HRESULT.  
  
##  <a name="create"></a>CD2DBitmap::Create  
 Crea un CD2DBitmap.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametri  
 `pRenderTarget`  
 Puntatore alla destinazione di rendering.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. In caso contrario, restituisce un codice di errore HRESULT.  
  
##  <a name="destroy"></a>CD2DBitmap::Destroy  
 Elimina un oggetto CD2DBitmap.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DBitmap::Detach  
 Disconnette l'interfaccia risorse dall'oggetto  
  
```  
ID2D1Bitmap* Detach();
```  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a interfaccia risorse scollegato.  
  
##  <a name="get"></a>CD2DBitmap::Get  
 Restituisce l'interfaccia ID2D1Bitmap  
  
```  
ID2D1Bitmap* Get();
```  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a un'interfaccia ID2D1Bitmap o NULL se l'oggetto non è ancora inizializzato.  
  
##  <a name="getdpi"></a>CD2DBitmap::GetDPI  
 Restituire i punti per pollice (DPI) della bitmap  
  
```  
CD2DSizeF GetDPI() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 DPI orizzontale e verticale della bitmap.  
  
##  <a name="getpixelformat"></a>CD2DBitmap::GetPixelFormat  
 Recupera la modalità di alfa e formato pixel della bitmap  
  
```  
D2D1_PIXEL_FORMAT GetPixelFormat() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Il formato pixel e alpha modalità della bitmap.  
  
##  <a name="getpixelsize"></a>CD2DBitmap::GetPixelSize  
 Restituisce la dimensione, in unità dipendenti dalla periferica (pixel), dell'immagine bitmap  
  
```  
CD2DSizeU GetPixelSize() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Le dimensioni, in pixel, della bitmap...  
  
##  <a name="getsize"></a>CD2DBitmap::GetSize  
 Restituisce la dimensione, in pixel indipendenti dal dispositivo (DIP), dell'immagine bitmap  
  
```  
CD2DSizeF GetSize() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 Dimensione, in DIP, della bitmap.  
  
##  <a name="isvalid"></a>CD2DBitmap::IsValid  
 Verifica la validità della risorsa  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valore restituito  
 TRUE se la risorsa è valido. in caso contrario FALSE.  
  
##  <a name="m_bautodestroyhbmp"></a>CD2DBitmap::m_bAutoDestroyHBMP  
 TRUE se m_hBmpSrc deve essere eliminato; in caso contrario FALSE.  
  
```  
BOOL m_bAutoDestroyHBMP;  
```  
  
##  <a name="m_hbmpsrc"></a>CD2DBitmap::m_hBmpSrc  
 Handle di bitmap di origine.  
  
```  
HBITMAP m_hBmpSrc;  
```  
  
##  <a name="m_lpsztype"></a>CD2DBitmap::m_lpszType  
 Tipo di risorsa.  
  
```  
LPCTSTR m_lpszType;  
```  
  
##  <a name="m_pbitmap"></a>CD2DBitmap::m_pBitmap  
 Archivia un puntatore a un oggetto ID2D1Bitmap.  
  
```  
ID2D1Bitmap* m_pBitmap;  
```  
  
##  <a name="m_sizedest"></a>CD2DBitmap::m_sizeDest  
 Dimensione di destinazione bitmap.  
  
```  
CD2DSizeU m_sizeDest;  
```  
  
##  <a name="m_strpath"></a>CD2DBitmap::m_strPath  
 Del file botmap.  
  
```  
CString m_strPath;  
```  
  
##  <a name="m_uiresid"></a>CD2DBitmap::m_uiResID  
 ID della risorsa bitmap  
  
```  
UINT m_uiResID;  
```  
  
##  <a name="operator_id2d1bitmap_star"></a>CD2DBitmap::operator ID2D1Bitmap *  
 Restituisce l'interfaccia ID2D1Bitmap  
  
```  
operator ID2D1Bitmap*();
```   
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a un'interfaccia ID2D1Bitmap o NULL se l'oggetto non è ancora inizializzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Classi](../../mfc/reference/mfc-classes.md)
