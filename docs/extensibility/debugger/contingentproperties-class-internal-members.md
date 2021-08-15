---
description: Contiene proprietà aggiuntive per un oggetto System.Threading.Tasks.Task.
title: Classe ContingentProperties - Membri interni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 81ba8eded541cd9db41c891cae8cc6fc86eb1ff9ddd6034070bdb10101d626a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452498"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties : membri interni
Contiene proprietà aggiuntive per un <xref:System.Threading.Tasks.Task> oggetto .

 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questi membri interni dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

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
- [Estensioni interne parallele per l'.NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
