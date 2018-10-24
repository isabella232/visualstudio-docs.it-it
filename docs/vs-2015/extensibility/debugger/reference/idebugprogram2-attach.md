---
title: IDebugProgram2::Attach | Microsoft Docs
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
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c64b4839d2f16adfcf40b082d54f60a95d7a468
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881640"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Collega al programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pCallback`  
 [in] Un' [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) oggetto da utilizzare per la notifica degli eventi di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. La tabella seguente illustra alcuni possibili codici di errore.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Il programma specificato è già collegato al debugger.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Si è verificata una violazione della sicurezza durante la procedura di collegamento.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un programma desktop non è possibile collegare il debugger.|  
  
## <a name="remarks"></a>Note  
 Un motore di debug (DE) non chiama mai questo metodo per connettersi a un programma. Se la Germania è in esecuzione nello spazio degli indirizzi del programma, il [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) viene chiamato il metodo. Se l'esecuzione DE nel gestore di sessione debug (SDM) addressspace, il [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) viene chiamato il metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

