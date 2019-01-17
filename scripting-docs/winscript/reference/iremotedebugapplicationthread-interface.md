---
title: IRemoteDebugApplicationThread Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplicationThread interface
ms.assetid: 062bb997-7b9e-4945-bfbe-d5b92d5cb707
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f502749453e1701c8e6e52e69745408fdcd9812d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349712"
---
# <a name="iremotedebugapplicationthread-interface"></a>Interfaccia IRemoteDebugApplicationThread
Rappresenta un thread di esecuzione all'interno di una determinata applicazione.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IRemoteDebugApplicationThread` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IRemoteDebugApplicationThread::GetSystemThreadId](../../winscript/reference/iremotedebugapplicationthread-getsystemthreadid.md)|Restituisce un identificatore dipendente dal sistema operativo associato al thread.|  
|[IRemoteDebugApplicationThread::GetApplication](../../winscript/reference/iremotedebugapplicationthread-getapplication.md)|Restituisce l'oggetto di applicazione associato a questo thread.|  
|[IRemoteDebugApplicationThread::EnumStackFrames](../../winscript/reference/iremotedebugapplicationthread-enumstackframes.md)|Restituisce un enumeratore per gli stack frame associato a questo thread.|  
|[IRemoteDebugApplicationThread::GetDescription](../../winscript/reference/iremotedebugapplicationthread-getdescription.md)|Ottiene la descrizione e lo stato di questo thread.|  
|[IRemoteDebugApplicationThread::SetNextStatement](../../winscript/reference/iremotedebugapplicationthread-setnextstatement.md)|Forza continuare l'esecuzione più vicino possibile al contesto di codice specificato, nel contesto del frame specificato.|  
|[IRemoteDebugApplicationThread::GetState](../../winscript/reference/iremotedebugapplicationthread-getstate.md)|Ottiene lo stato di questo thread.|  
|[IRemoteDebugApplicationThread::Suspend](../../winscript/reference/iremotedebugapplicationthread-suspend.md)|Sospende il thread.|  
|[IRemoteDebugApplicationThread::Resume](../../winscript/reference/iremotedebugapplicationthread-resume.md)|Riprende il thread.|  
|[IRemoteDebugApplicationThread::GetSuspendCount](../../winscript/reference/iremotedebugapplicationthread-getsuspendcount.md)|Restituisce il conteggio di sospensione per il thread.|