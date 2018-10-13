---
title: IDebugQueryEngine2 | Microsoft Docs
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
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 747457a93c7cd4da5efe305b0d7f07432fd880b2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307579"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia consente la sessione di debug manager (SDM) recuperare un'interfaccia che rappresenta il motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per gli oggetti che implementano le interfacce DE più comuni (ad esempio [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), e [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) in ordine per consentire l'accesso per il [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) dell'interfaccia della DE stesso.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) su un'interfaccia DE tipica per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugQueryEngine2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Ottiene un'interfaccia (DE) del motore di debug personalizzato.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia viene in genere implementata nell'oggetto che implementa il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per supportare l'ordine della causalità avanzando istruzione per le funzioni, vale a dire quando il debugger è uscita da una funzione, il funzione successiva da eseguire potrebbe non essere la precedente funzione nello stack, ma una funzione in un altro thread completamente. Per una definizione di "causalità", vedere la [glossario del Debugger di Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

