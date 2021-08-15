---
description: Questo articolo descrive i membri interni della classe System.Runtime.CompilerServices.AsyncTaskMethodBuilder.
title: Struttura AsyncTaskMethodBuilder - Membri interni
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 451696422e43cb257beb879980206b6c97f022743cf5ffd28eb40938d331460c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121434681"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Struttura AsyncTaskMethodBuilder - membri interni
In questo argomento vengono descritti i membri interni della <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe . Per informazioni generali su questa classe, vedere <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> l'argomento di riferimento.

 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questi membri interni dal .NET Framework, in Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membri interni

|Nome|Descrizione|
|----------|-----------------|
|[ObjectIdForDebugger - proprietà](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore nel debugger.|
|[m_builder campo](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Rappresenta l'oggetto generatore generico a cui delega questa istanza non generica.|

## <a name="see-also"></a>Vedi anche
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Estensioni interne parallele per l'.NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
