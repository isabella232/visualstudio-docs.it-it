---
title: Metodo GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8d038c8c67731fe1bff9ec705b5ddf416807a57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353713"
---
# <a name="gettaskschedulersfordebugger-method"></a>Metodo GetTaskSchedulersForDebugger
Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib. dll*)

 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Valore restituito
 Una matrice di tutti i <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi in questo <xref:System.AppDomain>.

## <a name="remarks"></a>Note
 Questo metodo non è thread-safe e non è consigliabile utilizzare contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler>. Chiamare questo metodo da un debugger solo quando il debugger ha sospeso tutti gli altri thread.

## <a name="see-also"></a>Vedere anche
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)