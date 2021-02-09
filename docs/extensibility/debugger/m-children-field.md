---
title: Campo m_children | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12bf76c5c9b62184a74006ddf288c7e581215ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925284"
---
# <a name="m_children-field"></a>Campo m_children
Elenco di attività figlio registrate con questa attività.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib.dll*)

 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Osservazioni
 Mentre l'attività è in esecuzione, solo il thread che esegue l'attività deve accedere a questa matrice.

 Se l'attività viene completata, gli altri thread possono accedere a questo campo purché non aggiungano nulla o non rimuovano nulla.

## <a name="see-also"></a>Vedi anche
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
