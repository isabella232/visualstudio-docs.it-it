---
description: L'attività è in esecuzione ma non è ancora stata completata.
title: TASK_STATE_EXECUTED campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: b99471317dd54c4a088af9a9f7d25d9b889a1b2a4a6c2e491d31cbf0e65c79ad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306257"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED campo
L'attività è in esecuzione ma non è ancora stata completata.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Osservazioni
 Se il [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) contiene questo valore, la <xref:System.Threading.Tasks.Task.Status%2A> proprietà restituisce <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Vedi anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
