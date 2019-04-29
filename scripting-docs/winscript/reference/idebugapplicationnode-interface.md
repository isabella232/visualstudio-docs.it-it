---
title: IDebugApplicationNode Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be864fdb9468668633322066bbbcf11569e4eb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822425"
---
# <a name="idebugapplicationnode-interface"></a>Interfaccia IDebugApplicationNode
Il `IDebugApplicationNode` interfaccia estende la funzionalità del `IDebugDocumentProvider` interfaccia, fornendo un contesto all'interno di un albero di progetto.  
  
 Oltre ai metodi ereditati da `IDebugDocumentProvider`, il `IDebugApplicationNode` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Enumera i nodi figlio del nodo dell'applicazione.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Restituisce il nodo padre del nodo dell'applicazione.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Imposta il provider di documento per questo nodo dell'applicazione.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Fa sì che questa applicazione per rilasciare tutti i riferimenti e passare a uno stato inattivo.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Aggiunge questo nodo dell'applicazione all'albero di progetto specificato.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Rimuove questo nodo dell'applicazione dall'albero del progetto.|