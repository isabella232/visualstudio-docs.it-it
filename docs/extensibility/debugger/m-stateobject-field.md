---
description: Oggetto che rappresenta i dati che verranno utilizzati dall'azione.
title: m_stateObject campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df510fafbfe3ed6e71e9b5290fb1df0b02ae1d39
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903957"
---
# <a name="m_stateobject-field"></a>m_stateObject campo
Oggetto che rappresenta i dati che verranno utilizzati dall'azione.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Osservazioni
 Questo è il `state` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore. È anche il campo di supporto per la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> proprietà .

## <a name="see-also"></a>Vedere anche
- [Classe di attività](../../extensibility/debugger/task-class-internal-members.md)
