---
description: Delegato che rappresenta il codice da eseguire nell'oggetto System. Threading. Tasks. Task.
title: Campo m_action | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be180bf50c61869aab889c731e40d8d43ffb7300
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094653"
---
# <a name="m_action-field"></a>campo m_action
Delegato che rappresenta il codice da eseguire nell' <xref:System.Threading.Tasks.Task> oggetto.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Osservazioni
 Si tratta del `action` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore.

## <a name="see-also"></a>Vedi anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
