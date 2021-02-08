---
title: Classe TaskScheduler-membri interni | Microsoft Docs
description: Informazioni sui membri interni della classe System. Threading. Tasks. TaskScheduler che consentono di implementare un debugger personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0ed72efb383e216d5998c2231a472b8d29f9ec4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837450"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler-membri interni
Questo articolo descrive i membri interni della <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe che consentono di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere l' <xref:System.Threading.Tasks.TaskScheduler> articolo di riferimento.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Members

### <a name="methods"></a>Metodi

|Nome|Descrizione|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera una matrice di tutte le attività pianificate.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi.|

## <a name="remarks"></a>Commenti

## <a name="see-also"></a>Vedi anche
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Interni di estensioni parallele per la .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
