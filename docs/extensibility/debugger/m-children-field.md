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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 17f009c25ce6de66a6ac4ce0ac2b1f304dd22a72
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709804"
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

 Se l'attività viene completata, altri thread possono accedere a questo campo purché non vi accedono o rimuovono alcun elemento.

## <a name="see-also"></a>Vedi anche
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
