---
title: Elementi interni delle estensioni in parallelo per .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0437363dd7d45b95a04a9e58edd45229f14b4c93
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695219"
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