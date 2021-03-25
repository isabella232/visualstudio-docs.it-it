---
description: Questo argomento descrive i membri interni della classe System. Runtime. CompilerServices. AsyncVoidMethodBuilder.
title: Struttura AsyncVoidMethodBuilder-membri interni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4097bce1f7fd90c5b73a3bb450a873561d76d9c1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055336"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struttura AsyncVoidMethodBuilder-membri interni
In questo argomento vengono descritti i membri interni della <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Per informazioni generali su questa classe, vedere l' <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> argomento di riferimento.

 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questi membri interni dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.

## <a name="syntax"></a>Sintassi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membri interni

|Nome|Descrizione|
|----------|-----------------|
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco il generatore al debugger.|
|[campo m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Rappresenta l'oggetto inizializzato in modo differito utilizzato dal debugger per identificare in modo univoco il generatore.|

## <a name="see-also"></a>Vedi anche
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Interni di estensioni parallele per la .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
