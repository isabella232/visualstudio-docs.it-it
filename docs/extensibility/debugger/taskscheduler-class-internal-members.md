---
title: Classe TaskScheduler - Membri interni | Microsoft Docs
description: Informazioni sui membri interni della classe System.Threading.Tasks.TaskScheduler che consentono di implementare un debugger personalizzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58b370a6742387f7493e4c6357cffd05f2bd88a5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900148"
---
# <a name="taskscheduler-class---internal-members"></a>Classe TaskScheduler - Membri interni
Questo articolo descrive i membri interni della classe che consentono <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> di implementare un debugger personalizzato. Per informazioni generali su questa classe, vedere <xref:System.Threading.Tasks.TaskScheduler> l'articolo di riferimento.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questi membri interni dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

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

## <a name="see-also"></a>Vedere anche
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Estensioni interne parallele per l'.NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
