---
title: Classe TaskScheduler - Membri Interni Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712573"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - Membri interni
In questo articolo vengono descritti <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> i membri interni della classe che consentono di implementare un debugger personalizzato. Per informazioni generali su questa <xref:System.Threading.Tasks.TaskScheduler> classe, vedere l'articolo di riferimento.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Membri

### <a name="methods"></a>Metodi

|Nome|Descrizione|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera una matrice di tutte le attività pianificate.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matrice <xref:System.Threading.Tasks.TaskScheduler> di tutti gli oggetti attualmente attivi.|

## <a name="remarks"></a>Osservazioni

## <a name="see-also"></a>Vedere anche
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Elementi interni delle estensioni parallele per .NET FrameworkParallel extension internals for the .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
