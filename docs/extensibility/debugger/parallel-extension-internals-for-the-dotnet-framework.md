---
title: Elementi interni delle estensioni in parallelo per .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ecc13be90259c68fa4d37daa5139b27b4ea8c7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351486"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Elementi interni delle estensioni parallele per .NET Framework
In questa sezione vengono descritti i tipi interni, metodi e campi delle classi che consentono di implementano un debugger personalizzato per le estensioni parallele a .NET Framework.

## <a name="in-this-section"></a>Contenuto della sezione
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md) vengono descritti i membri dati interni del <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.

 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) vengono descritti i membri dati interni del <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.

 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) vengono descritti i membri dati interni del `System.Threading.Tasks.ContingentProperties` classe.

 [Struttura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struttura.

 [AsyncTaskMethodBuilder\<TResult > struttura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struttura.

 [Struttura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struttura.

## <a name="see-also"></a>Vedere anche
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Estendibilità del debugger Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)