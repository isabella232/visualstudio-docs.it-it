---
title: 'Metodo ijsdebugdatatarget:: GetThreadContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50e2bdb7b8720549aac5e5b3c4cebffc4b7ae892
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090064"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>Metodo IJsDebugDataTarget::GetThreadContext
Recupera il contesto del thread specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `threadId`  
 [in] Thread in esecuzione nel processo di destinazione.  
  
 `contextFlags`  
 [in] Specifica i flag di contesto. Si tratta dello stesso il campo ContextFlags di CONTEXT (per altre informazioni, vedere Winnt. h, cercare CONTEXT_ALL).  
  
 `contextSize`  
 [in] Le dimensioni del buffer specificata da pContext.  
  
 `pContext`  
 [out] Riceve la struttura del CONTEXT specifica della piattaforma nel buffer specificato da pContext.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)