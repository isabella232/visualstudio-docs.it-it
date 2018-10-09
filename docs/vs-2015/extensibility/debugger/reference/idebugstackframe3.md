---
title: IDebugStackFrame3 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f032ac6b5fb348916c51f8cc98e1726b0795e21
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518813"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugStackFrame3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe3).  
  
Questa interfaccia estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) per gestire le eccezioni intercettate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia nello stesso oggetto che implementa il [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfaccia per supportare le eccezioni intercettate.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) su un `IDebugStackFrame2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati da [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Gestisce un'eccezione per lo stack frame corrente prima la gestione delle eccezioni regolari.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Restituisce un contesto di codice se si verifica uno svuotamento dello stack.|  
  
## <a name="remarks"></a>Note  
 Un'eccezione intercettata significa che un debugger può elaborare un'eccezione prima di qualsiasi routine di gestione delle eccezioni normale vengono chiamati dal runtime. Intercettare un'eccezione essenzialmente significa mettere in fase di esecuzione fingendo che vi sia un gestore di eccezioni presente anche quando non esiste.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) viene chiamato durante tutti gli eventi di callback di eccezione normale (l'unica eccezione è se si esegue il debug in modalità mista di codice gestito e codice non gestito, nel qual caso non è possibile intercettare l'eccezione durante il ultima callback). Se non implementa la Germania `IDebugStackFrame3`, o la Germania restituisce un errore da IDebugStackFrame3::`InterceptCurrentException` (ad esempio `E_NOTIMPL`), quindi il debugger l'eccezione verrà gestita normalmente.  
  
 Mediante l'intercettazione di un'eccezione, il debugger può consentire all'utente di apportare modifiche allo stato del programma in fase di debug e riprendere l'esecuzione nel punto in cui è stata generata l'eccezione.  
  
> [!NOTE]
>  Le eccezioni intercettate sono consentite solo nel codice gestito, vale a dire, in un programma che viene eseguito in Common Language Runtime (CLR).  
  
 Un motore di debug indica che lo supporta intercettazione delle eccezioni tramite l'impostazione "metricExceptions" su un valore pari a 1 in fase di esecuzione usando il `SetMetric` (funzione). Per altre informazioni, vedere [helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
