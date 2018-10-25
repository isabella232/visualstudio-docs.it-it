---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1fa934610778479551d411a4b231a4b190f29bcd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937408"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
Specifica come interpretare un ID di processo nel [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Membri  
 AD_PROCESS_ID_SYSTEM  
 ID del processo è un identificatore di sistema. Usare il `ProcessId.dwProcessId` campo le [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura.  
  
 AD_PROCESS_ID_GUID  
 ID del processo è un GUID. Usare la `ProcessId.guidProcessId` campo il `AD_PROCESS_ID` struttura.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `ProcessIdType` membro del [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura per identificare il tipo di ID del processo che è contenuto nella struttura. Determina come interpretare il `ProcessId` union nella struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)