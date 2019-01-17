---
title: IDebugApplicationNodeEvents Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0396ed90437a98c8ee398f3c3acb0aeb5ddc77e2
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348412"
---
# <a name="idebugapplicationnodeevents-interface"></a>Interfaccia IDebugApplicationNodeEvents
Specifica l'interfaccia evento per l'interfaccia `IDebugApplicationNode`.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugApplicationNodeEvents` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Gestisce l'evento quando un nodo figlio viene aggiunto a un oggetto nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Gestisce l'evento quando un nodo figlio viene rimosso da un oggetto nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Gestisce un evento per indicare che l'oggetto nodo dell'applicazione di debug è stato scollegato da un nodo padre.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Gestisce un evento per indicare che l'oggetto nodo dell'applicazione di debug è stato collegato a un nodo padre.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)