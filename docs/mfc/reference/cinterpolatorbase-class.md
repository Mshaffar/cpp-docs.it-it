---
title: Classe CInterpolatorBase | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
dev_langs:
- C++
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: 6bf2a6b11f64b5ec7e7f2e311c62e7f1ce9144d8
ms.contentlocale: it-it
ms.lasthandoff: 10/09/2017

---
# <a name="cinterpolatorbase-class"></a>Classe CInterpolatorBase
Implementa un callback, chiamato dall'API di animazione quando deve essere calcolato un nuovo valore di una variabile di animazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;  
```  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Costruisce il `CInterpolatorBase` oggetto.|  
  
### <a name="public-methods"></a>Metodi pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CInterpolatorBase::CreateInstance](#createinstance)|Crea un'istanza di `CInterpolatorBase` e archivia un puntatore a un interpolatore personalizzato che gli eventi.|  
|[CInterpolatorBase::GetDependencies](#getdependencies)|Ottiene le dipendenze dell'interpolatore. Esegue l'override di `CUIAnimationInterpolatorBase::GetDependencies`.|  
|[CInterpolatorBase::GetDuration](#getduration)|Ottiene la durata dell'interpolatore. Esegue l'override di `CUIAnimationInterpolatorBase::GetDuration`.|  
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Ottiene il valore finale a cui punta l'interpolatore. Esegue l'override di `CUIAnimationInterpolatorBase::GetFinalValue`.|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Il valore a un offset specificato esegue l'interpolazione (esegue l'override `CUIAnimationInterpolatorBase::InterpolateValue`.)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Crea un'interpolazione la velocità a un offset specificato (esegue l'override `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Archivia un puntatore a un interpolatore personalizzato che gli eventi.|  
|[CInterpolatorBase::SetDuration](#setduration)|Imposta la durata dell'interpolatore (esegue l'override `CUIAnimationInterpolatorBase::SetDuration`.)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Imposta il valore iniziale dell'interpolatore e velocità. Esegue l'override di `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.|  
  
## <a name="remarks"></a>Note  
 Questo gestore viene creato e passato a `IUIAnimationTransitionFactory::CreateTransition` quando un `CCustomTransition` oggetto viene creato come parte del processo di inizializzazione di animazione (avviato da `CAnimationController::AnimateGroup`). In genere non è necessario utilizzare questa classe direttamente, sufficiente routs tutti gli eventi per un `CCustomInterpolator`-cui puntatore viene passato al costruttore della classe derivata `CCustomTransition`.  
  
## <a name="inheritance-hierarchy"></a>Gerarchia di ereditarietà  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** afxanimationcontroller.h  
  
##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase  
 Costruisce l'oggetto CInterpolatorBase.  
  
```  
CInterpolatorBase();
```  
  
##  <a name="createinstance"></a>CInterpolatorBase::CreateInstance  
 Crea un'istanza di CInterpolatorBase e archivia un puntatore a un interpolatore personalizzato che gli eventi.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,  
    IUIAnimationInterpolator** ppHandler);
```  
  
### <a name="parameters"></a>Parametri  
 `pInterpolator`  
 Puntatore a interpolatore personalizzato.  
  
 `ppHandler`  
 Output. Contiene un puntatore all'istanza di CInterpolatorBase quando la funzione restituisce.  
  
### <a name="return-value"></a>Valore restituito  
  
##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies  
 Ottiene le dipendenze dell'interpolatore.  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Parametri  
 `initialValueDependencies`  
 Output. Gli aspetti dell'interpolatore che dipendono dal valore iniziale passato a SetInitialValueAndVelocity.  
  
 `initialVelocityDependencies`  
 Output. Gli aspetti dell'interpolatore che dipendono da velocità iniziale passati a SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Output. Gli aspetti dell'interpolatore che dipendono dalla durata passati a SetDuration.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. Restituisce E_FAIL se CCustomInterpolator non è impostato o l'implementazione personalizzata restituisce FALSE dal metodo GetDependencies.  
  
##  <a name="getduration"></a>CInterpolatorBase::GetDuration  
 Ottiene la durata dell'interpolatore.  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parametri  
 `duration`  
 Output. La durata della transizione, in secondi.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. Restituisce E_FAIL se CCustomInterpolator non è impostato o l'implementazione personalizzata restituisce FALSE dal metodo GetDuration.  
  
##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue  
 Ottiene il valore finale a cui punta l'interpolatore.  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametri  
 `value`  
 Output. Il valore finale di una variabile alla fine della transizione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. Restituisce E_FAIL se CCustomInterpolator non è impostato o l'implementazione personalizzata restituisce FALSE dal metodo GetFinalValue.  
  
##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue  
 Il valore a un offset specificato esegue l'interpolazione  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametri  
 `offset`  
 L'offset dall'inizio della transizione. L'offset è sempre maggiore o uguale a zero e minore della durata della transizione. Questo metodo non viene chiamato se la durata della transizione è zero.  
  
 `value`  
 Output. Il valore interpolato.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. Restituisce E_FAIL se CCustomInterpolator non è impostato o l'implementazione personalizzata restituisce FALSE dal metodo InterpolateValue.  
  
##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity  
 Crea un'interpolazione la velocità a un offset specificato  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parametri  
 `offset`  
 L'offset dall'inizio della transizione. L'offset è sempre maggiore di o uguale a zero e minore o uguale alla durata della transizione. Questo metodo non viene chiamato se la durata della transizione è zero.  
  
 `velocity`  
 Output. La velocità della variabile in corrispondenza dell'offset.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. Restituisce E_FAIL se CCustomInterpolator non è impostato o l'implementazione personalizzata restituisce FALSE dal metodo InterpolateVelocity.  
  
##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator  
 Archivia un puntatore a un interpolatore personalizzato che gli eventi.  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>Parametri  
 `pInterpolator`  
 Puntatore a interpolatore personalizzato.  
  
##  <a name="setduration"></a>CInterpolatorBase::SetDuration  
 Imposta la durata dell'interpolatore  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parametri  
 `duration`  
 La durata della transizione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. Restituisce E_FAIL se CCustomInterpolator non è impostato o l'implementazione personalizzata restituisce FALSE dal metodo SetDuration.  
  
##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity  
 Imposta il valore iniziale dell'interpolatore e velocità.  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parametri  
 `initialValue`  
 Il valore della variabile all'inizio della transizione.  
  
 `initialVelocity`  
 La velocità della variabile all'inizio della transizione.  
  
### <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, viene restituito S_OK. Restituisce E_FAIL se CCustomInterpolator non è impostato o l'implementazione personalizzata restituisce FALSE dal metodo SetInitialValueAndVelocity.  
  
## <a name="see-also"></a>Vedere anche  
 [Classi](../../mfc/reference/mfc-classes.md)
