---
title: IDebugPortEx2::GetPortProcessId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9a3ccfb0fa0493ad435e5167dfaf921af6732296
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844720"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
Ottiene l'ID del processo della porta di se stesso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```csharp  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwProcessId`  
 [out] Restituisce l'ID del processo fisica della porta di se stesso.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Nel runtime di Win32, ad esempio, questo metodo in genere chiama la funzione Win32 `GetCurrentProcessId` per ottenere l'ID del processo fisico.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)