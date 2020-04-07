---
title: Metodo GetTaskSchedulersForDebugger . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738642"
---
# <a name="gettaskschedulersfordebugger-method"></a>Metodo GetTaskSchedulersForDebugger
Recupera una matrice <xref:System.Threading.Tasks.TaskScheduler> di tutti gli oggetti attualmente attivi.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valore restituito
 Matrice di <xref:System.Threading.Tasks.TaskScheduler> tutti gli oggetti attualmente <xref:System.AppDomain>attivi in questo oggetto .

## <a name="remarks"></a>Osservazioni
 Questo metodo non è thread-safe e non è consigliabile <xref:System.Threading.Tasks.TaskScheduler>utilizzarlo contemporaneamente ad altre istanze di . Chiamare questo metodo da un debugger solo quando il debugger ha sospeso tutti gli altri thread.

## <a name="see-also"></a>Vedere anche
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
