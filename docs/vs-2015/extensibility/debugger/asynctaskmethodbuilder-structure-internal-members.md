---
title: Struttura AsyncTaskMethodBuilder - membri interni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bfe640654c9de7daac9096aa4d75f5492a8a278
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969319"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Struttura AsyncTaskMethodBuilder - Membri interni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> classe. Per informazioni generali su questa classe, vedere il <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membri interni  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore del debugger.|  
|[campo m_builder](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Rappresenta l'oggetto generatore generico a cui questa istanza non generici delega.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
