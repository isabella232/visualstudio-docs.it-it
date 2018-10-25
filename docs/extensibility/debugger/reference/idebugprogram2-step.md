---
title: IDebugProgram2::Step | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 489a641e0f42f6e8e1720929775d8da3df08eeb8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948343"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Esegue un passaggio.  
  
> [!NOTE]
>  Questo metodo è deprecato. Usare la [passaggio](../../../extensibility/debugger/reference/idebugprocess3-step.md) metodo invece.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pThread`  
 [in] Un' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) oggetto che rappresenta il thread in corso rientri.  
  
 `sk`  
 [in] Un valore compreso il [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumerazione che specifica il tipo di passaggio.  
  
 `step`  
 [in] Un valore compreso il [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumerazione che specifica l'unità del passaggio (ad esempio, di istruzione o dell'istruzione).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In caso di qualsiasi sincronizzazione dei thread o comunicazione tra thread, altri thread nel programma deve essere eseguito quando un thread specifico è l'esecuzione di istruzioni.  
  
> [!WARNING]
>  Non inviare un evento di arresto o di un evento (sincrono) immediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante la gestione di questa chiamata; in caso contrario, il debugger potrebbe bloccarsi.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)