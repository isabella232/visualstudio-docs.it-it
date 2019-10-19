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
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577508"
---
# <a name="iscriptnode-interface"></a>Interfaccia IScriptNode
Un oggetto che implementa l'interfaccia `IScriptNode` rappresenta una pagina Web.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IScriptNode` espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indica se un oggetto è ancora attivo.|  
|[IScriptNode::CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Aggiunge un'istanza figlio di `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Aggiunge un scriptlet come istanza figlio di un `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Elimina l'albero degli oggetti.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Restituisce l'elemento figlio in corrispondenza dell'indice specificato nel nodo.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Restituisce un valore definito dall'applicazione che viene utilizzato per associare un scriptlet all'oggetto host.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Restituisce l'indice di un oggetto nell'elenco figlio dell'elemento padre.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Restituisce il linguaggio di scripting utilizzato dal nodo di script corrente.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Restituisce il numero di nodi figlio dell'oggetto `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Restituisce l'oggetto `IScriptNode` padre di un oggetto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce metodo Script ActiveX](../../winscript/reference/active-script-authoring-interfaces.md)