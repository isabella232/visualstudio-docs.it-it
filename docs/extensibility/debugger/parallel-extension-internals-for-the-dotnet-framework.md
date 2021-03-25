---
title: Interni di estensioni parallele per la .NET Framework | Microsoft Docs
description: Queste risorse descrivono i tipi interni, i metodi e i campi delle classi usate per implementare un debugger personalizzato per le estensioni parallele al .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aec52f354043dabb3bf816bbd35352f0c3a28bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067829"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Interni di estensioni parallele per la .NET Framework
In questa sezione vengono descritti i tipi, i metodi e i campi interni delle classi che consentono di implementare un debugger personalizzato per le estensioni parallele al .NET Framework.

## <a name="in-this-section"></a>Contenuto della sezione
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md) Descrive i membri dati interni della <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.

 [TaskScheduler (classe](../../extensibility/debugger/taskscheduler-class-internal-members.md) ) Descrive i membri dati interni della <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.

 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) Descrive i membri dati interni della `System.Threading.Tasks.ContingentProperties` classe.

 [Struttura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Descrive i membri interni della <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struttura.

 [La \<TResult> Struttura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) descrive i membri interni della <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struttura.

 [Struttura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Descrive i membri interni della <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struttura.

## <a name="see-also"></a>Vedi anche
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programmazione parallela](/dotnet/standard/parallel-programming/index)
