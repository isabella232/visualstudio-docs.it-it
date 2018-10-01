---
title: IDebugPortRequest2 | Microsoft Docs
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
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7873d3d73556bae671cc1150525eb3d08a136e27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47532623"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugPortRequest2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportrequest2).  
  
Questa interfaccia viene descritta una porta. Questa descrizione viene usata per aggiungere la porta a un fornitore di porte.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa in genere questa interfaccia nel processo di recupero di una porta di debug da un fornitore di porte.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene passata [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) per creare una porta di debug. Una chiamata a [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) restituisce questa interfaccia, che rappresenta la richiesta utilizzata per creare la porta in primo luogo.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi di `IDebugPortRequest2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Ottiene il nome della porta da creare.|  
  
## <a name="remarks"></a>Note  
 In genere, un motore di debug non interagisce con un fornitore di porte e non disporrà di alcun uso per questa interfaccia.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)

