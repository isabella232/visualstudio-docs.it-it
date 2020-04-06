---
title: m_children Campo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738420"
---
# <a name="m_children-field"></a>m_children campo
Elenco di attività figlio registrate con questa attività.

 **Spazio dei nomi:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Osservazioni
 Mentre l'attività è in esecuzione, solo il thread che esegue l'attività deve accedere a questa matrice.

 Se l'attività viene completata, altri thread possono accedere a questo campo purché non vi aggiustano o rimuovano nulla.

## <a name="see-also"></a>Vedere anche
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
