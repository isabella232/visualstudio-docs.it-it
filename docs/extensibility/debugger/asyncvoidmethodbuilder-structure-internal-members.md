---
title: Struttura AsyncVoidMethodBuilder - Membri interni . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739295"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder (struttura) - membri interni
In questo argomento vengono descritti <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> i membri interni della classe. Per informazioni generali su questa <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe, vedere l'argomento di riferimento.

 **Spazio dei nomi:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib.dll)

 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente è disponibile in Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membri interni

|Nome|Descrizione|
|----------|-----------------|
|[ObjectIdForDebugger (proprietà)](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore nel debugger.|
|[m_objectIdForDebugger campo](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Rappresenta l'oggetto inizializzato in modo lato utilizzato dal debugger per identificare in modo univoco questo generatore.|

## <a name="see-also"></a>Vedere anche
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Elementi interni delle estensioni parallele per .NET FrameworkParallel extension internals for the .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
