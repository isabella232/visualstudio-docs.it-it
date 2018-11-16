---
title: AsyncTaskMethodBuilder&lt;TResult&gt; struttura - membri interni | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 966a6ee224ac14707ed411e7e63c9473831c7003
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792346"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; struttura - membri interni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questo argomento vengono descritti i membri interni del <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> classe. Per informazioni generali su questa classe, vedere il <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> argomento di riferimento.  
  
 **Spazio dei nomi:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché non è possibile accedere a questi membri interni da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Membri interni  
  
|nome|Descrizione|  
|----------|-----------------|  
|[Proprietà ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Ottiene un oggetto che può essere utilizzato per identificare in modo univoco questo generatore del debugger.|  
|[campo m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Rappresenta l'inizializzazione differita compilate attività.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Elementi interni delle estensioni parallele per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

