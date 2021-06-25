---
description: Recupera una matrice di tutti gli oggetti System.Threading.Tasks.TaskScheduler attualmente attivi.
title: Metodo GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58cb913f5dbc729c297de8a34aa5dd4c3c99b48a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900915"
---
# <a name="gettaskschedulersfordebugger-method"></a>Metodo GetTaskSchedulersForDebugger
Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valore restituito
 Matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi in questo oggetto <xref:System.AppDomain> .

## <a name="remarks"></a>Commenti
 Questo metodo non è thread-safe e non deve essere utilizzato contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler> . Chiamare questo metodo da un debugger solo quando il debugger ha sospeso tutti gli altri thread.

## <a name="see-also"></a>Vedere anche
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
