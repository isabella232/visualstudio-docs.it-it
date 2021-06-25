---
description: Elenco di attività figlio registrate con questa attività.
title: m_children campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 311ab164551e46fbe1c30b5a6045a7993a900a67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901370"
---
# <a name="m_children-field"></a>m_children campo
Elenco di attività figlio registrate con questa attività.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Osservazioni
 Mentre l'attività è in esecuzione, solo il thread che esegue l'attività deve accedere a questa matrice.

 Se l'attività viene completata, altri thread possono accedere a questo campo purché non vi accedono o non vi rimuovono alcun elemento.

## <a name="see-also"></a>Vedere anche
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
