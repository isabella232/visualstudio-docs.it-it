---
title: Campo m_action | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d33d356f606dc2622647de53b50f5c677b3c14eb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330976"
---
# <a name="maction-field"></a>campo m_action
Delegato che rappresenta il codice da eseguire nel <xref:System.Threading.Tasks.Task> oggetto.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib. dll*)

 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Note
 Questo è il `action` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore.

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)