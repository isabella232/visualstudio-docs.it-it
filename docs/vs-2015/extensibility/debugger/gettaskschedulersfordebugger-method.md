---
title: Metodo GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152717"
---
# <a name="gettaskschedulersfordebugger-method"></a>Metodo GetTaskSchedulersForDebugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera una matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (in mscorlib.dll)  
  
 Poiché non è possibile accedere a questo membro interno dalla .NET Framework, nella Common Intermediate Language (CIL) viene fornita la sintassi seguente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Valore restituito  
 Matrice di tutti <xref:System.Threading.Tasks.TaskScheduler> gli oggetti attualmente attivi in questo oggetto <xref:System.AppDomain> .  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo non è thread-safe e non deve essere utilizzato contemporaneamente ad altre istanze di <xref:System.Threading.Tasks.TaskScheduler> . Deve essere chiamato da un debugger solo quando il debugger ha sospeso tutti gli altri thread.  
  
## <a name="see-also"></a>Vedere anche  
 [Classe TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
