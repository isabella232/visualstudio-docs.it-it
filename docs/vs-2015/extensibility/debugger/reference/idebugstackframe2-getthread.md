---
title: 'IDebugStackFrame2:: GetThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetThread
helpviewer_keywords:
- IDebugStackFrame2::GetThread
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9dd05e553ab5353b6ebf39970437c21c498caaff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62548092"
---
# <a name="idebugstackframe2getthread"></a>IDebugStackFrame2::GetThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il thread associato a un stack frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetThread (   
   IDebugThread2** ppThread  
);  
```  
  
```csharp  
int GetThread (   
   out IDebugThread2 ppThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppThread`  
 out Restituisce un oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) che rappresenta il thread.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
