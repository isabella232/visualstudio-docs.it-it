---
title: Campo m_children | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fefeaf07c923a5fefa282efcd96948b2d907cca1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704644"
---
# <a name="mchildren-field"></a>campo m_children
L'elenco delle attività figlio che sono registrati con questa attività.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in *mscorlib. dll*)

 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Note
 Durante l'esecuzione dell'attività, solo il thread che esegue l'attività deve accedere a questa matrice.

 Se l'attività è stata completata, altri thread può accedere a questo campo, purché non aggiunge nulla ad esso o rimuovere qualsiasi elemento da quest'ultimo.

## <a name="see-also"></a>Vedere anche
- [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)