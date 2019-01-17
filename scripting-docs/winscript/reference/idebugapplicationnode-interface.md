---
title: IDebugApplicationNode Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d7bd38a0fbbdd596f6a1f6bb040190dddca78bf9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348997"
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