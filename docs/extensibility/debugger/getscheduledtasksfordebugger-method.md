---
description: Recupera una matrice di tutte le attività pianificate.
title: Metodo GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e63c7fefe387c0bd7980980eb43a0f78b5c4ffb5a878af3d22b16b4f77806ba7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342739"
---
# <a name="getscheduledtasksfordebugger-method"></a>Metodo GetScheduledTasksForDebugger
Recupera una matrice di tutte le attività pianificate.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Valore restituito
 Matrice di tutte le attività pianificate. Ogni attività è in esecuzione o ha terminato l'esecuzione.

## <a name="remarks"></a>Commenti
 Questo metodo non è thread-safe e non deve essere utilizzato contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler> . Chiamare questo metodo da un debugger solo quando il debugger ha sospeso tutti gli altri thread.

## <a name="see-also"></a>Vedi anche
- [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
