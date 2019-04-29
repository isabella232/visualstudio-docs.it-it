---
title: IEnumRemoteDebugApplications::Reset | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Reset
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Reset
ms.assetid: a2c03728-999f-400c-bf40-4ced6cd88410
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8cf00fa40f00e511f56763e6a497ea477bf686d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962275"
---
# <a name="ienumremotedebugapplicationsreset"></a>IEnumRemoteDebugApplications::Reset
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
 [Interfaccia IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)