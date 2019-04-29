---
title: IEnumDebugApplicationNodes::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Clone
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Clone
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28ccf1805c1213bd01b1628c73e1dce5500ad8f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951515"
---
# <a name="ienumdebugapplicationnodesclone"></a>IEnumDebugApplicationNodes::Clone
Crea un enumeratore che contiene lo stesso stato dell'enumeratore corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pperddp`  
 [out] Restituisce il `IEnumDebugApplicationNodes` interfaccia del clone dell'enumeratore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo crea un enumeratore che contiene lo stesso stato dell'enumeratore corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)