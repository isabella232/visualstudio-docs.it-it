---
title: Metodo GetScheduledTasksForDebugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b68f8f238c180d4152d99b42f8ac075ef6dd3e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990628"
---
# <a name="getscheduledtasksfordebugger-method"></a>Metodo GetScheduledTasksForDebugger
Recupera una matrice di tutte le attività pianificate.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in *mscorlib. dll*)  
  
 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```csharp  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valore restituito  
 Matrice di tutte le attività pianificate. Ogni attività sono in esecuzione o ha completato l'esecuzione.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è thread-safe e non è consigliabile utilizzare contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler>. Chiamare questo metodo da un debugger solo quando il debugger ha sospeso tutti gli altri thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)