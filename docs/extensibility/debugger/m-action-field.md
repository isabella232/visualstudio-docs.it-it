---
description: Delegato che rappresenta il codice da eseguire nell'oggetto System.Threading.Tasks.Task.
title: m_action campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0b2c5b4927a07bcb05c0ada97d4aed9f6c6da8c6cc65e21aa65fc3e40af1996c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121361054"
---
# <a name="m_action-field"></a>m_action campo
Delegato che rappresenta il codice da eseguire <xref:System.Threading.Tasks.Task> nell'oggetto .

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Osservazioni
 Questo è il `action` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore.

## <a name="see-also"></a>Vedi anche
- [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)
