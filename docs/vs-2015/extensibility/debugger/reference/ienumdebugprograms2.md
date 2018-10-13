---
title: IEnumDebugPrograms2 | Microsoft Docs
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
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbb01738876eb342fecb83f7f6d09c850ee89636
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49247637"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia enumera i programmi in esecuzione nella sessione di debug corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il motore di debug (DE) implementa questa interfaccia per fornire un elenco di programmi in fase di debug per la Germania.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Le chiamate di Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) per ottenere questa interfaccia. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) non viene usato da Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IEnumDebugPrograms2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[avanti](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Recupera un determinato numero di programmi in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignora un numero specificato di programmi in una sequenza di enumerazione.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ottiene il numero di programmi in un enumeratore.|  
  
## <a name="remarks"></a>Note  
 Visual Studio Usa questa interfaccia per:  
  
-   Popolare la **moduli** finestra (chiamando [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) e quindi chiamando [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) su ciascun programma).  
  
-   Popolare la **Connetti a processo** elenco (chiamando `IDebugProcess2::EnumPrograms` e quindi chiamare [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) su ogni [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaccia per ottenere un [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interface).  
  
-   Generare un elenco di DEs che è possibile eseguire il debug di ogni programma nel processo (tramite [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Applicare gli aggiornamenti di modifica e Continuazione per ogni programma (chiamando IDebugProcess2::EnumPrograms e quindi chiamare [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)

