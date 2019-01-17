---
title: Interfaccia IScriptNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8897d783f8a101b41dd7263061604fb1d82ec56
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344616"
---
# <a name="iscriptnode-interface"></a>Interfaccia IScriptNode
Un oggetto che implementa il `IScriptNode` interfaccia rappresenta una pagina Web.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IScriptNode` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indica se un oggetto è ancora attivo.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Aggiunge un'istanza figlio di `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Aggiunge un scriptlet come istanza figlio di un `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Elimina l'albero degli oggetti.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Restituisce l'elemento figlio in corrispondenza dell'indice specificato nel nodo.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Restituisce un valore definito dall'applicazione che consente di associare l'oggetto host di scriptlet.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Restituisce l'indice di un oggetto nell'elenco di elementi figlio dell'elemento padre.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Restituisce il linguaggio di scripting utilizzato dal nodo corrente dello script.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Restituisce il numero di nodi figlio del `IScriptNode` oggetto.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Restituisce il `IScriptNode` oggetto padre di un oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)