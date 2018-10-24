---
title: IDebugThread2::GetThreadId | Microsoft Docs
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
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 89253a38970d58bcdeed41f2e2447b2137ef648c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49832277"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene l'identificatore di thread di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetThreadId (   
   DWORD* pdwThreadId  
);  
```  
  
```csharp  
int GetThreadId (   
   out uint pdwThreadId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwThreadId`  
 [out] Restituisce l'identificatore di thread di sistema.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un ID thread viene usato per identificare un thread tra tutti gli altri thread in un processo.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un semplice `CProgram` oggetto che implementa le [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interfaccia.  
  
```cpp#  
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {     
   *pdwThreadId = GetCurrentThreadId();    
   return NOERROR;    
}    
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

