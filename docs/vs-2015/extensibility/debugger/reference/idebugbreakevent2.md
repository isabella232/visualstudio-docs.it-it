---
title: IDebugBreakEvent2 | Microsoft Docs
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
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1a2f9fede9119b4db0baf45e61213bcb2b5b67c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177762"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia indica al gestore di sessione di debug (SDM) che un'interruzione asincrona è stata completata correttamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 La Germania implementa questa interfaccia per supportare le interruzioni utente in un programma. Il [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaccia deve essere implementata per lo stesso oggetto di questa interfaccia (Usa il modello SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per l'accesso il `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) quando l'utente ha richiesto il programma in fase di debug per essere messo in pausa. Quando il programma è stata sospesa, la Germania invia il `IDebugBreakEvent2` evento. Questo evento viene inviato tramite il [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funzione di callback fornita dal modello SDM quando associato al programma in fase di debug.  
  
## <a name="remarks"></a>Note  
 Ad esempio, un utente può selezionare il **Interrompi tutto** comando le **Debug** menu per interrompere un programma che esegue un ciclo infinito. Il modello SDM indica al programma di arrestare chiamando [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). L'invio di DE `IDebugBreakEvent2` quando infine si arresterà.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

