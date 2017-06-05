---
title: "Metodo InterfaceTraits::CastToUnknown | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CastToUnknown (metodo)"
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo InterfaceTraits::CastToUnknown
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Supporta l'infrastruttura WRL e non può essere utilizzata direttamente dal proprio codice.  
  
## Sintassi  
  
```  
template<  
   typename T  
>  
static __forceinline IUnknown* CastToUnknown(  
   _In_ T* ptr  
);  
```  
  
#### Parametri  
 `T`  
 Tipo del parametro `ptr`.  
  
 `ptr`  
 Puntatore al tipo `T`.  
  
## Valore restituito  
 Puntatore a IUnknown da cui è derivato `Base`.  
  
## Note  
 Il cast specifica il puntatore a un puntatore a IUnknown.  
  
 Per ulteriori informazioni su `Base`, vedere la sezione pubblica Typedef in [Struttura InterfaceTraits](../windows/interfacetraits-structure.md).  
  
## Requisiti  
 **Header:** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## Vedere anche  
 [Struttura InterfaceTraits](../windows/interfacetraits-structure.md)   
 [Spazio dei nomi Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)