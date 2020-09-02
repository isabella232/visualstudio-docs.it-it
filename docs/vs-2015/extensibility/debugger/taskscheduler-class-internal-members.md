---
title: Classe TaskScheduler-membri interni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 427a84b3dcda0471f5ec9d71883a5a8e859bb92d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176693"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - Membri interni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni della <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere l' <xref:System.Threading.Tasks.TaskScheduler> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler  
       extends System.Object  
```  
  
## <a name="members"></a>Membri  
  
### <a name="methods"></a>Metodi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera una matrice di tutte le attività pianificate.|  
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi.|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
