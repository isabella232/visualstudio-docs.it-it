---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086593"
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