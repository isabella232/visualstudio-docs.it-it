---
title: TASK_STATE_WAITING_ON_CHILDREN campo Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27b9963db54d939b3d509da451478c20dbe0e7d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712577"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN campo
L'attività ha terminato l'esecuzione del delegato ed è implicitamente in attesa del completamento delle attività figlio associate.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Osservazioni
 Se il [campo m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene <xref:System.Threading.Tasks.Task.Status%2A> questo <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>valore, la proprietà restituisce .

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
