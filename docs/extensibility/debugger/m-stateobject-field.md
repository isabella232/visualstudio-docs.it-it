---
title: Campo m_stateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c49682d43236f66b3acbef630f1d81b32e97dab2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889491"
---
# <a name="mstateobject-field"></a>campo m_stateObject
Oggetto che rappresenta i dati che verrà usato l'azione.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib. dll*)

 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Note
 Questo è il `state` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore. È anche il campo sottostante per il <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> proprietà.

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)