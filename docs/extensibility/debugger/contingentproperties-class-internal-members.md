---
description: Contiene proprietà aggiuntive per un oggetto System. Threading. Tasks. Task.
title: Classe ContingentProperties-membri interni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2303318c7a5f36027ce7709c5b09b5846fc6fab6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154977"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties-membri interni
Contiene proprietà aggiuntive per un <xref:System.Threading.Tasks.Task> oggetto.

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Members

### <a name="fields"></a>Campi

|Nome|Descrizione|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Elenco di attività figlio registrate con questa attività.|

## <a name="remarks"></a>Commenti
 Il .NET Framework inizializza i campi di questa classe solo quando sono necessari.

## <a name="see-also"></a>Vedi anche
- [Interni di estensioni parallele per la .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
