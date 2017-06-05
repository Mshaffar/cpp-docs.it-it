---
title: Funzioni dello spazio dei nomi Concurrency::Graphics::Direct3D | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs:
- C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 63cf872bd5ade28115a0eac92304554f125c8dd5
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funzioni dello spazio dei nomi Concurrency::Graphics::Direct3D
||||  
|-|-|-|  
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|  
|[make_texture](#make_texture)|[msad4](#msad4)|  

 
##  <a name="get_sampler"></a>get_sampler  
 Ottenere l'interfaccia D3D campionatore stato determinato tasto di scelta rapida consente di visualizzare che rappresenta l'oggetto specificato campionatore.  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parametri  
 `_Av`  
 Una vista D3D tasti di scelta rapida in cui viene creato lo stato del campionatore D3D.  
  
 `_Sampler`  
 Un oggetto di prova per cui viene creato l'interfaccia di stati campionatore D3D sottostante.  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a interfaccia IUnknown corrispondente allo stato campionatore D3D che rappresenta il campionatore specificato.  
  
##  <a name="get_texture"></a>get_texture  
 Ottiene l'interfaccia di trama Direct3D sottostante specificato [trama](texture-class.md) oggetto.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const writeonly_texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
```  
  
### <a name="parameters"></a>Parametri  
 `value_type`  
 Il tipo di elemento della trama.  
  
 `_Rank`  
 Il numero di dimensioni della trama.  
  
 `_Texture`  
 Una trama o visualizzazione di trama associato il accelerator_view per il quale viene restituito l'interfaccia di trama Direct3D sottostante.  
  
### <a name="return-value"></a>Valore restituito  
 Puntatore a interfaccia IUnknown corrispondente a trama Direct3D sottostante la trama.  
  
##  <a name="make_sampler"></a>make_sampler  
 Creare un campionatore da un puntatore a interfaccia D3D campionatore dello stato.  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parametri  
 `_D3D_sampler`  
 Puntatore a interfaccia IUnknown dello stato del campionatore D3D campionatore da creare.  
  
### <a name="return-value"></a>Valore restituito  
 Un campionatore rappresenta lo stato di campionatore D3D fornito.  
  
##  <a name="make_texture"></a>make_texture  
 Crea un [trama](texture-class.md) oggetto utilizzando i parametri specificati.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
texture<value_type, _Rank> make_texture(
    const Concurrency::accelerator_view& _Av,  
    _In_ IUnknown* _D3D_texture,  
    DXGI_FORMAT _View_format = DXGI_FORMAT_UNKNOWN) restrict(cpu);
```  
  
### <a name="parameters"></a>Parametri  
 `value_type`  
 Tipo degli elementi di trama.  
  
 `_Rank`  
 Il numero di dimensioni della trama.  
  
 `_Av`  
 Una vista D3D tasti di scelta rapida in cui si desidera creare la trama.  
  
 `_D3D_texture`  
 Puntatore a interfaccia IUnknown della trama D3D per creare la trama da.  
  
 `_View_format`  
 Il formato DXGI da utilizzare per le viste create da questo trama. Passare DXGI_FORMAT_UNKNOWN (predefinito) per derivare il formato dal formato sottostante di _D3D_texture e value_type del modello. Il formato specificato deve essere compatibile con il formato di _D3D_texture sottostante.  
  
### <a name="return-value"></a>Valore restituito  
 Una trama utilizzando la trama D3D fornita.  
  
##  <a name="msad4"></a>msad4  
 Confronta un valore di riferimento di 4 byte e un valore di origine a 8 byte e accumula un vettore di 4 somme. Ogni somma corrisponde alla somma mascherata delle differenze assolute di allineamenti diversi byte tra il valore di riferimento e il valore di origine.  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>Parametri  
 `_Reference`  
 Matrice di riferimento di 4 byte in un valore uint  
  
 `_Source`  
 Matrice di origine di 8 byte in un vettore di due valori uint.  
  
 `_Accum`  
 Un vettore di 4 valori da aggiungere alla somma mascherata delle differenze assolute dei allineamenti diversi byte tra il valore di riferimento e il valore di origine.  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce un vettore di 4 somme. Ogni somma corrisponde alla somma mascherata delle differenze assolute di allineamenti diversi byte tra il valore di riferimento e il valore di origine.  

## <a name="requirements"></a>Requisiti  
 **Intestazione:** amp_graphics.h  
  
 **Namespace:** Concurrency::graphics::direct3d 

## <a name="see-also"></a>Vedere anche  
 [Spazio dei nomi Concurrency::graphics::direct3d](concurrency-graphics-direct3d-namespace.md)
