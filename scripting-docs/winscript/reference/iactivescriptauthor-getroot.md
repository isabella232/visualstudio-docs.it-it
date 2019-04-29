---
title: IActiveScriptAuthor::GetRoot | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetRoot
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetRoot
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6cdb3246ccae2eabb34696162f67e82a60374550
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955107"
---
# <a name="iactivescriptauthorgetroot"></a>IActiveScriptAuthor::GetRoot
Restituisce il `IScriptNode` radice dell'albero di script dell'autore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppsp`  
 [out] L'indirizzo di una variabile che riceve un puntatore al `IScriptNode` interfaccia del nodo radice.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)