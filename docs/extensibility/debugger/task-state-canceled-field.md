---
title: TASK_STATE_CANCELED Campo Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712751"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED campo
L'attività è stata annullata prima di raggiungere lo stato di esecuzione oppure ne ha confermato l'annullamento e completato senza eccezioni.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Osservazioni
 Se il [campo m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene <xref:System.Threading.Tasks.Task.Status%2A> questo <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>valore, la proprietà restituisce .

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
