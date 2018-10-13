---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
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
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eee8e8f205cb1dbc220c50dd1f7abd342c942483
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284063"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Motori di debug non implementano questo metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStackFrame`  
 [in] Un' [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) oggetto che rappresenta il frame dello stack.  
  
 `ppLogicalThread`  
 [out] Restituisce un `IDebugLogicalThread2` interfaccia che rappresenta il thread logico associato. Un'implementazione del motore di debug debba impostare un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 Eseguire il debug restituiscono sempre le implementazioni di motore `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)

