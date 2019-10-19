---
title: 'IDebugApplicationNode:: alleghi | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574778"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Aggiunge il nodo dell'applicazione all'albero del progetto specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdanParent`  
 in Albero del progetto in cui deve essere aggiunto il nodo dell'applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo aggiunge il nodo dell'applicazione all'albero del progetto, usando `pdanParent` come padre. Se `pdanParent` è `NULL`, il nodo dell'applicazione sarà il nodo di primo livello.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugApplicationNode::D etach](../../winscript/reference/idebugapplicationnode-detach.md)    
 [Interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)