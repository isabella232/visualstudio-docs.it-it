---
title: Classe ContingentProperties-membri interni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739104"
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

## <a name="remarks"></a>Osservazioni
 Il .NET Framework inizializza i campi di questa classe solo quando sono necessari.

## <a name="see-also"></a>Vedere anche
- [Interni di estensioni parallele per la .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
