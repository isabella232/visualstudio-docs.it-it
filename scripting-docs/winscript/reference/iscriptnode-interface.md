---
title: Interfaccia IScriptNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 13bf20f9e1e642b948ddaa72ae9dca7bb457fba2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786774"
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