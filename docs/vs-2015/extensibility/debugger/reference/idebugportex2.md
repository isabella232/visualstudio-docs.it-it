---
title: IDebugPortEx2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab8036061f51a63079b43f04abe64564ed141fee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212830"
---
# <a name="idebugportex2"></a>IDebugPortEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia consente la sessione di debug controllo manager (SDM) i programmi e i processi in esecuzione su una porta.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia nello stesso oggetto che implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) nel `IDebugPort2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortEx2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Avvia un file eseguibile.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Riprende l'esecuzione di un processo.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se un processo può essere terminato.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termina un processo.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ottiene l'ID del processo della porta di se stesso.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ottiene un programma associato a un nodo di programma.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia è in genere privata tra il modello SDM e il fornitore della porta personalizzata.  
  
 Se si desidera, un motore di debug (DE) può cercare questa interfaccia [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia passata al [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) allo stesso modo [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) per avviare il programma. Tuttavia, non è un requisito, e un CRI possono eseguire tutte le attività per avviare il programma di richiesta.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

