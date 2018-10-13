---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
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
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55a13bbfa3b2addbeb05b343dae5f598ddaac687
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260741"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

DEPRECATO. NON USARE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pMDMProgram`  
 [in] Il [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia che rappresenta il programma a cui connettersi.  
  
 `pCallback`  
 [in] Il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interfaccia da utilizzare per inviare gli eventi di debug per il modello SDM.  
  
 `dwReason`  
 [in] Un valore compreso il [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumerazione che specifica il motivo per il collegamento.  
  
## <a name="return-value"></a>Valore restituito  
 Un'implementazione deve sempre restituire `E_NOTIMPL`.  
  
## <a name="remarks"></a>Note  
  
> [!WARNING]
>  A partire [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL`. Vedere le [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interfaccia di amministrazione di un approccio alternativo se il nodo programma deve indicare non è possibile collegare o se il nodo di programma è semplicemente l'impostazione del programma `GUID`. In caso contrario, implementare il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) (metodo).  
  
## <a name="prior-to-visual-studio-2005"></a>Prima di Visual Studio 2005  
 Questo metodo deve essere implementata solo se la Germania viene eseguito nello spazio degli indirizzi del programma in fase di debug. In caso contrario, questo metodo deve restituire `S_FALSE`.  
  
 Quando questo metodo viene chiamato, la Germania è necessario inviare il [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) oggetto dell'evento, se non si sono già stato inviato per questa istanza del [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaccia, così come il [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oggetti evento. Il [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) oggetto dell'evento viene inviato se le `dwReason` parametro `ATTACH_REASON_LAUNCH`.  
  
 La Germania è necessario chiamare il [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) metodo sul [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto fornito dal [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventi dell'oggetto e devono archiviare il GUID del programma nei dati dell'istanza per il `IDebugProgram2` oggetto implementato dal DE.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Collegare](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)

