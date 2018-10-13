---
title: Metodo GetScheduledTasksForDebugger | Microsoft Docs
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
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57d71dff0404b8bcea7f7274b943925eb45e0830
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201981"
---
# <a name="getscheduledtasksfordebugger-method"></a>Metodo GetScheduledTasksForDebugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una matrice di tutte le attività pianificate.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib. dll)  
  
 Poiché è possibile accedere a questo membro interno da .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valore restituito  
 Matrice di tutte le attività pianificate. Ogni attività sono in esecuzione o ha completato l'esecuzione.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è thread-safe e non deve essere utilizzato contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler> deve essere chiamato da un debugger solo quando il debugger ha sospeso tutti gli altri thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)

