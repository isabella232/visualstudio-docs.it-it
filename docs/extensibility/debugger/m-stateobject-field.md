---
title: m_stateObject Campo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fed70f2eda19ad96454a83217c20c046809f3034
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738380"
---
# <a name="m_stateobject-field"></a>m_stateObject campo
Oggetto che rappresenta i dati che verranno utilizzati dall'azione.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Osservazioni
 Questo è `state` il <xref:System.Threading.Tasks.Task.%23ctor%2A> parametro nel costruttore. È anche il campo di <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> sostegno per la proprietà.

## <a name="see-also"></a>Vedere anche
- [Classe Task](../../extensibility/debugger/task-class-internal-members.md)
