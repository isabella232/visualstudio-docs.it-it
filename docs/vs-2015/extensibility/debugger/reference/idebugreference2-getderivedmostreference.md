---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6baff17ba485b45a239d2acb0af2b765844fa35c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914008"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il riferimento più derivato di un riferimento. Riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppDerivedMost`  
 [out] Restituisce un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto che rappresenta la proprietà più derivato.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## <a name="remarks"></a>Note  
 Ad esempio, se questa proprietà descrive un oggetto che implementa `ClassRoot` ma che è effettivamente un'istanza di `ClassDerived` che è derivato da `ClassRoot`, questo metodo restituisce un' [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) oggetto che rappresenta un riferimento al `ClassDerived` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

