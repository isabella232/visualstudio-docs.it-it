---
title: Interfaccia ISimpleConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571797"
---
# <a name="isimpleconnectionpoint-interface"></a>Interfaccia ISimpleConnectionPoint
Fornisce un modo semplice per descrivere ed enumerare gli eventi generati in un determinato punto di connessione. Questa interfaccia consente inoltre di associare facilmente un oggetto `IDispatch` a tali eventi. Questa interfaccia viene implementata da Process Debug Manager (PDM) e utilizzata dai motori di script.  
  
 Questa interfaccia è disponibile dal `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `ISimpleConnectionPoint` espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Stabilisce una connessione tra l'oggetto punto di connessione semplice e il sink del client.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Restituisce il DISPID e il nome per ogni evento in un intervallo di eventi specificato.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Restituisce il numero di eventi esposti in questa interfaccia.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Termina una connessione consultiva precedentemente stabilita tramite `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)