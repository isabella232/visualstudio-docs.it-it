---
title: Classe TaskScheduler - membri interni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 865e12819a5e7325886c0f7f5d8425a6b3d2e393
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331336"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - membri interni
Questo articolo descrive i membri interni del <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classi che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere il <xref:System.Threading.Tasks.TaskScheduler> articolo di riferimento.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib. dll*)

 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).

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
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi.|

## <a name="remarks"></a>Note

## <a name="see-also"></a>Vedere anche
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)