---
title: Interfaccia ISimpleConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a756fa3f933f4adff56c41a86aee19a0a2a93aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346410"
---
# <a name="isimpleconnectionpoint-interface"></a>Interfaccia ISimpleConnectionPoint
Fornisce un modo semplice per la descrizione e l'enumerazione agli eventi generati in un punto di connessione specifica. Questa interfaccia consente anche di associare facilmente un `IDispatch` oggetto tali eventi. Questa interfaccia viene implementata dal processo di Debug Manager (PDM) e utilizzata da motori di script.  
  
 Questa interfaccia è disponibile da `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `ISimpleConnectionPoint` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Stabilisce una connessione tra l'oggetto punto di connessione semplici e il sink del client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Restituisce il DISPID e il nome per ogni evento in un intervallo specificato di eventi.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Restituisce il numero di eventi esposti su questa interfaccia.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Termina una connessione consultiva precedentemente stabilita tramite `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)