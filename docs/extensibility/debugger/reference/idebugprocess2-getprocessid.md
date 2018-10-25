---
title: IDebugProcess2::GetProcessId | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a643e980e0a0d03b6c6d2634890dc5aba61b1f8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869093"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Ottiene il GUID del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```csharp  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pguidProcessId`  
 [out] Restituisce il GUID del processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'identificatore univoco globale (GUID, Globally Unique Identifier) identifica questo processo da tutti gli altri processi in esecuzione nel sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)