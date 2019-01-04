---
title: Campo m_action | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b41c5d0ae7733a2a9256882852b9016d8e05e0bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944457"
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
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)