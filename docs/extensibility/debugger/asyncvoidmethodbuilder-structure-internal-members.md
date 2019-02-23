---
title: Struttura AsyncVoidMethodBuilder - membri interni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c51d76d38680945eaccbd3ace256813668c51
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716805"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struttura AsyncVoidMethodBuilder - membri interni
In questo argomento vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> classe. Per informazioni generali su questa classe, vedere il <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> argomento di riferimento.

 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Assembly:** mscorlib (in mscorlib. dll)

 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).

## <a name="syntax"></a>Sintassi

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Membri interni

|nome|Descrizione|
|----------|-----------------|
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore del debugger.|
|[campo m_objectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Rappresenta l'oggetto inizializzato in modo differito usato dal debugger per identificare in modo univoco questo generatore.|

## <a name="see-also"></a>Vedere anche
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)