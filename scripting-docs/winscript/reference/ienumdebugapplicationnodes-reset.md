---
title: IEnumDebugApplicationNodes::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugApplicationNodes.Reset
apilocation:
- pdm.dll
helpviewer_keywords:
- IEnumDebugApplicationNodes::Reset
ms.assetid: 56ecdafe-ff11-461a-92e1-93254a49f1a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 960f980bda330eaf14cc498e8bf804649023ba39
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156893"
---
# <a name="ienumdebugapplicationnodesreset"></a>IEnumDebugApplicationNodes::Reset
Reimposta una sequenza di enumerazione all'inizio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo reimposta una sequenza di enumerazione all'inizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IEnumDebugApplicationNodes](../../winscript/reference/ienumdebugapplicationnodes-interface.md)