---
title: IDebugReference2::GetSize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::GetSize
helpviewer_keywords:
- IDebugReference2::GetSize
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69924f0094753e87ac2f169a3348d59999e43ddc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911303"
---
# <a name="idebugreference2getsize"></a>IDebugReference2::GetSize
Ottiene la dimensione, espressa in byte, del valore del riferimento. Riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSize`  
 [out] Restituisce la dimensione, espressa in byte, del valore del riferimento.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)