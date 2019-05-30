---
title: Campo TASK_STATE_CANCELED | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e8b2906c2a8061a7153533036fcab7de82ca1d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348398"
---
# <a name="taskstatecanceled-field"></a>Campo TASK_STATE_CANCELED
L'attività è stata annullata prima che ha raggiunto lo stato di esecuzione o confermata relativo annullamento e completamento senza eccezioni.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib. dll)

 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Note
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene questo valore, il <xref:System.Threading.Tasks.Task.Status%2A> restituisce proprietà <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)