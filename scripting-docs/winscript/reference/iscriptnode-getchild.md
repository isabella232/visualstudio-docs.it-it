---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 78b5c84c6ed9b3de9593f0d6ff02df93a0e9ba77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787130"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Restituisce l'elemento figlio in corrispondenza dell'indice specificato nel nodo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `isn`  
 [in] L'indice dell'elemento figlio del padre.  
  
 `ppsn`  
 [out] L'indirizzo di una variabile che riceve un puntatore al `IScriptNode` interfaccia dell'istanza figlio.  
  
 Per `IScriptNode` gli oggetti che rappresentano una pagina Web, questo parametro restituisce un oggetto che contiene un blocco di script.  
  
 Per `IScriptEntry` oggetti che specificano un blocco di script, questo parametro restituisce un oggetto che specifica una funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Per la `IScriptEntry` oggetti che specificano un oggetto funzione e per `IScriptScriptlet` oggetti, questo metodo ha esito negativo perché non sono presenti voci figlio.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)