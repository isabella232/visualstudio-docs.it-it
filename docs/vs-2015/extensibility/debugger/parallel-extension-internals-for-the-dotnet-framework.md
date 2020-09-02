---
title: Interni di estensioni parallele per la .NET Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42c472190469e7d008fa8c525f50eabfaf37053f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65680931"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Elementi interni delle estensioni parallele per .NET Framework
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questa sezione vengono descritti i tipi, i metodi e i campi interni delle classi che consentono di implementare un debugger personalizzato per le estensioni parallele al .NET Framework.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Classe Task](../../extensibility/debugger/task-class-internal-members.md)  
 Descrive i membri dati interni della <xref:System.Threading.Tasks.Task?displayProperty=fullName> classe.  
  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Descrive i membri dati interni della <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> classe.  
  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Descrive i membri dati interni della `System.Threading.Tasks.ContingentProperties` classe.  
  
 [Struttura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Descrive i membri interni della <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struttura.  
  
 [\<TResult>Struttura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Descrive i membri interni della <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struttura.  
  
 [Struttura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Descrive i membri interni della <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struttura.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Programmazione parallela](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
