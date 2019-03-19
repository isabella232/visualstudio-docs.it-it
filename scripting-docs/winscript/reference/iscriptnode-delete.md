---
title: IScriptNode::Delete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41bf932b242865b1deac4c61db400f973bd0b00c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145005"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Elimina questo albero degli oggetti.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Dopo il `Delete` metodo viene chiamato, il [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) metodo deve indicare tale nodo di script non è attivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)