---
title: IActiveScriptErrorDebug::GetStackFrame | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptErrorDebug.GetStackFrame
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptErrorDebug::GetStackFrame
ms.assetid: a6f43102-68c5-46f5-a4df-fa3aaf53a967
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aecda7be418f2a89fb39bc1d754c8e94cf1130bd
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152288"
---
# <a name="iactivescripterrordebuggetstackframe"></a>IActiveScriptErrorDebug::GetStackFrame
Fornisce lo stack frame che è attiva per gli errori di runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetStackFrame(  
   IDebugStackFrame**  ppdsf  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppdsf`  
 [out] Il frame dello stack dell'errore.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo fornisce stack frame sul quale è in vigore per errori di run-time.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)