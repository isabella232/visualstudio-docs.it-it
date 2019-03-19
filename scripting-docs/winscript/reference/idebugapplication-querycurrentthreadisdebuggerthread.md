---
title: IDebugApplication::QueryCurrentThreadIsDebuggerThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.QueryCurrentThreadIsDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::QueryCurrentThreadIsDebuggerThread
ms.assetid: e22ad8a4-a8be-423d-80f2-28256a7448ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ed53bcdb5e0d613a757c0c60f4791b0c59e3476
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154257"
---
# <a name="idebugapplicationquerycurrentthreadisdebuggerthread"></a>IDebugApplication::QueryCurrentThreadIsDebuggerThread
Determina se il thread corrente in esecuzione il thread del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT QueryCurrentThreadIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo ha avuto esito positivo e il thread di esecuzione corrente è il thread del debugger.|  
|`S_FALSE`|Il thread di esecuzione corrente non è il thread del debugger.|  
  
## <a name="remarks"></a>Note  
 Questo metodo determina se il thread di esecuzione corrente è il thread del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)