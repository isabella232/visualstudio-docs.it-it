---
title: IEnumDebugFrameInfo2 | Microsoft Docs
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
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e343b8caabe2a09943ccc4cd068a62598dea548
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532625"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IEnumDebugFrameInfo2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugframeinfo2).  
  
Questa interfaccia enumera [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per fornire un elenco di strutture che descrive lo stack di chiamate corrente.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate di Visual Studio [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) per ottenere questa interfaccia ogni volta che un punto di interruzione, eccezione o arresto si verifica in un programma in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugFrameInfo2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un numero specificato di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignora un numero specificato di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture in una sequenza di enumerazione.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ottiene il numero di [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture nell'enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio ottiene questa interfaccia come primo passaggio per la gestione di un punto di interruzione, eccezioni o generati dall'utente pausa attivata il programma sottoposto a debug. L'elenco delle [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) strutture rappresenta lo stack di chiamate corrente, con la chiamata di funzione corrente all'inizio dell'elenco e la funzione meno recente chiamare alla fine dell'elenco. Ogni `FRAMEINFO` rappresenta uno stack frame, un contesto in cui possono essere valutate espressioni e variabili locali preso in esame.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
