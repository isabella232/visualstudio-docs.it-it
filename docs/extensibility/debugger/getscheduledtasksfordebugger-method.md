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
ms.openlocfilehash: d25acf7d40c2f1f78dcf2102ca612289426c5f80
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073331"
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
