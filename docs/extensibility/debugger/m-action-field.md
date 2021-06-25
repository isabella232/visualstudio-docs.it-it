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
ms.workload:
- vssdk
ms.openlocfilehash: 838494eb612ffaa18931e42227619b22bc297b4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901474"
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

## <a name="see-also"></a>Vedere anche
- [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)
