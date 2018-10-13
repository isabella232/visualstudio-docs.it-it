---
title: IDebugPortSupplier3 | Microsoft Docs
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
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ae9b1911d92c8fe2e9a55b7737c37db44aa9d441
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49284414"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia consente a un chiamante determinare se un fornitore di porte può mantenere le porte (mediante la scrittura su disco) tra le chiamate del debugger e quindi ottenere un elenco di queste porte mantenute.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per il supporto di persistenza o il salvataggio di informazioni relative alla porta al disco. Questa interfaccia deve essere implementata nell'oggetto stesso come il [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) nel `IDebugPortSupplier2` interfaccia per ottenere questa interfaccia.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi ereditati dal [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia, questa interfaccia supporta i seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Restituisce se il fornitore della porta può mantenere le porte (mediante la scrittura su disco) tra le chiamate del debugger.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Restituisce un oggetto che può essere utilizzato per enumerare attraverso tutte le porte che sono stati scritti su disco per il fornitore della porta.|  
  
## <a name="remarks"></a>Note  
 Se un fornitore di porte può rendere persistenti le porte tra le chiamate, deve implementare questa interfaccia. Le porte devono essere caricate quando il fornitore della porta viene creata un'istanza e scritto su disco quando il fornitore della porta viene eliminato definitivamente.  
  
 In genere, un motore di debug non interagisce con un fornitore di porte e non disporrà di alcun uso per questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)

