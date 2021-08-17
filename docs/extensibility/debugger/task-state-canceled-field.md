---
description: L'attività è stata annullata prima di raggiungere lo stato di esecuzione oppure ne ha confermato l'annullamento e l'operazione è stata completata senza eccezioni.
title: TASK_STATE_CANCELED campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c6e20f40111f88ad304e5ce86cf4f60a8449418b7d83b6ae9879c6598f0c7f0a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338085"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED campo
L'attività è stata annullata prima di raggiungere lo stato di esecuzione oppure ne ha confermato l'annullamento e l'operazione è stata completata senza eccezioni.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Osservazioni
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene questo valore, la <xref:System.Threading.Tasks.Task.Status%2A> proprietà restituisce <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Vedi anche
- [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)
