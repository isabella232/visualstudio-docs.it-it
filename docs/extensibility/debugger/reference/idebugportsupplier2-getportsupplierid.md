---
title: IDebugPortSupplier2::GetPortSupplierId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eaff656f91d958b4c31fd57295f5361a85b6841e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954319"
---
# <a name="idebugportsupplier2getportsupplierid"></a>IDebugPortSupplier2::GetPortSupplierId
Ottiene l'identificatore fornitore di porte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortSupplierId(   
   GUID* pguidPortSupplier  
);  
```  
  
```csharp  
HRESULT GetPortSupplierId(   
   out Guid pguidPortSupplier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pguidPortSupplier`  
 [out] Restituisce il GUID del fornitore della porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)