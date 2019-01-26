---
title: Metodo GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76229d86c973c9ef512ecf5039ae420085129160
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029245"
---
# <a name="gettaskschedulersfordebugger-method"></a>Metodo GetTaskSchedulersForDebugger
Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in *mscorlib. dll*)  
  
 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```csharp  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valore restituito  
 Una matrice di tutti i <xref:System.Threading.Tasks.TaskScheduler> gli oggetti che sono attualmente attivi in questo <xref:System.AppDomain>.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è thread-safe e non è consigliabile utilizzare contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler>. Chiamare questo metodo da un debugger solo quando il debugger ha sospeso tutti gli altri thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)