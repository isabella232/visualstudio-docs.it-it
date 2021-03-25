---
description: Recupera una matrice di tutti gli oggetti System. Threading. Tasks. TaskScheduler attualmente attivi.
title: Metodo GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d024e44dee8e7513d862e3d299c2ed2b9e53cd5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054855"
---
# <a name="gettaskschedulersfordebugger-method"></a>Metodo GetTaskSchedulersForDebugger
Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valore restituito
 Matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi in questo oggetto <xref:System.AppDomain> .

## <a name="remarks"></a>Commenti
 Questo metodo non è thread-safe e non deve essere utilizzato contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler> . Chiamare questo metodo da un debugger solo quando il debugger ha sospeso tutti gli altri thread.

## <a name="see-also"></a>Vedi anche
- [TaskScheduler (classe)](../../extensibility/debugger/taskscheduler-class-internal-members.md)
