---
title: IDebugAsyncOperation::QueryIsComplete | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de686f146fded1e4b53914a1de706025f6680ab6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160157"
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
Determina se l'operazione di debug è stata completata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|L'operazione è stata completata.|  
|`S_FALSE`|L'operazione non è stata completata.|  
  
## <a name="remarks"></a>Note  
 Questo metodo determina se l'operazione di debug è stata completata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)