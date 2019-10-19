---
title: 'IScriptNode:: GetChild | Microsoft Docs'
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
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573559"
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
 in Indice dell'elemento figlio nell'elemento padre.  
  
 `ppsn`  
 out Indirizzo di una variabile che riceve un puntatore all'interfaccia `IScriptNode` dell'istanza figlio.  
  
 Per `IScriptNode` oggetti che rappresentano una pagina Web, questo parametro restituisce un oggetto che contiene un blocco di script.  
  
 Per `IScriptEntry` oggetti che specificano un blocco di script, questo parametro restituisce un oggetto che specifica una funzione.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Per `IScriptEntry` oggetti che specificano un oggetto funzione e per `IScriptScriptlet` oggetti, questo metodo ha esito negativo perché non sono presenti voci figlio.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)