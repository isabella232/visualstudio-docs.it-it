---
title: Interfaccia IDebugApplicationNodeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574722"
---
# <a name="idebugapplicationnodeevents-interface"></a>Interfaccia IDebugApplicationNodeEvents
Specifica l'interfaccia evento per l'interfaccia `IDebugApplicationNode`.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugApplicationNodeEvents` espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Gestisce l'evento quando viene aggiunto un nodo figlio a un oggetto del nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Gestisce l'evento quando un nodo figlio viene rimosso da un oggetto del nodo dell'applicazione di debug.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Gestisce un evento che indica che l'oggetto del nodo dell'applicazione di debug è stato scollegato da un nodo padre.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Gestisce un evento che indica che l'oggetto del nodo dell'applicazione di debug è stato associato a un nodo padre.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)