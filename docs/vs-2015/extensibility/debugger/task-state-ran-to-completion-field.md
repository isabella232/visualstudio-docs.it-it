---
title: Campo TASK_STATE_RAN_TO_COMPLETION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f7d5f05a077e5243d5de52c210ae65dbfe3b2850
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428027"
---
# <a name="task_state_ran_to_completion-field"></a>Campo TASK_STATE_RAN_TO_COMPLETION
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'esecuzione dell'attività è stata completata correttamente.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)  
```  
  
## <a name="remarks"></a>Osservazioni  
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene questo valore, la <xref:System.Threading.Tasks.Task.Status%2A> proprietà restituisce <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Vedere anche  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
