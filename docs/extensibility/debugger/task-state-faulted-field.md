---
description: L'attività è stata completata a causa di un'eccezione non gestita.
title: Campo TASK_STATE_FAULTED | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5a8113f6145706d2863a4f0060a8627952eb0b3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223186"
---
# <a name="task_state_faulted-field"></a>Campo TASK_STATE_FAULTED
L'attività è stata completata a causa di un'eccezione non gestita.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Osservazioni
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) campo contiene questo valore, la <xref:System.Threading.Tasks.Task.Status%2A> proprietà restituisce <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Vedi anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
