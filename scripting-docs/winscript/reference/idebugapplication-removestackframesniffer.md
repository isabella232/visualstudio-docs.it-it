---
title: 'IDebugApplication:: RemoveStackFrameSniffer | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveStackFrameSniffer
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveStackFrameSniffer
ms.assetid: 00304b88-e435-4b87-a331-44e7492eb32d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605daf51214ba5af9d6010b28be9569453ca7962
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571121"
---
# <a name="idebugapplicationremovestackframesniffer"></a>IDebugApplication::RemoveStackFrameSniffer
Rimuove un provider di enumeratori stack frame da questa applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT RemoveStackFrameSniffer(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCookie`  
 in Cookie restituito dal metodo `AddStackFrameSniffer` quando è stato aggiunto il provider dell'enumeratore stack frame.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Il metodo `RemoveStackFrameSniffer` rimuove un provider di enumeratori stack frame da questa applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)   
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IDebugStackFrameSniffer](../../winscript/reference/idebugstackframesniffer-interface.md)