---
description: L'attività è stata annullata prima di raggiungere lo stato di esecuzione oppure ne è stato confermato l'annullamento e completata senza eccezioni.
title: TASK_STATE_CANCELED campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90b3c048edb4e52a426a2fd40d8bfd31168fea7d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900174"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED campo
L'attività è stata annullata prima di raggiungere lo stato di esecuzione oppure ne è stato confermato l'annullamento e completata senza eccezioni.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Osservazioni
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene questo valore, la <xref:System.Threading.Tasks.Task.Status%2A> proprietà restituisce <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
