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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: fad86acc86043e58bfa68f0cf8687b7c439b7ad6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160348"
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
 Si tratta del `state` parametro nel <xref:System.Threading.Tasks.Task.%23ctor%2A> costruttore. È anche il campo di supporto per la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> proprietà .

## <a name="see-also"></a>Vedi anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
