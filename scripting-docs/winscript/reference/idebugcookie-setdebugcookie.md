---
title: IDebugCookie::SetDebugCookie | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCookie.SetDebugCookie
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugCookie::SetDebugCookie
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c83c1331a95e48afa02b0b37557ca5bd042261d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974475"
---
# <a name="idebugcookiesetdebugcookie"></a>IDebugCookie::SetDebugCookie
Imposta il cookie di debug dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwDebugAppCookie`  
 [in] Cookie che identifica l'applicazione di debug.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo imposta il cookie dell'applicazione di debug, che consente a più di un debugger possa connettersi a un processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugCookie](../../winscript/reference/idebugcookie-interface.md)