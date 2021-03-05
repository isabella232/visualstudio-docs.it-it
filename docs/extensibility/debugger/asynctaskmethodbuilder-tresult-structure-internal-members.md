---
description: Questo argomento descrive i membri interni della classe System. Runtime. CompilerServices. AsyncTaskMethodBuilder.
title: '&lt;Struttura AsyncTaskMethodBuilder TResult &gt; -membri interni | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35e1ca4d19727383bdd7c957bc59fd6b6568c9f5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145651"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>&lt;Struttura AsyncTaskMethodBuilder TResult &gt; -membri interni
In questo argomento vengono descritti i membri interni della <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> classe. Per informazioni generali su questa classe, vedere l' <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> argomento di riferimento.

 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membri interni

|Nome|Descrizione|
|----------|-----------------|
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco il generatore al debugger.|
|[campo m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Rappresenta l'attività compilata in modo differito.|

## <a name="see-also"></a>Vedi anche
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Interni di estensioni parallele per la .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
