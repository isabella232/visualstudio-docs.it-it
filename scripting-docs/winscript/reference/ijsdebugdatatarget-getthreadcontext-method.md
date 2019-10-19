---
title: 'Metodo metodo ijsdebugdatatarget:: GetThreadContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577650"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>Metodo IJsDebugDataTarget::GetThreadContext
Recupera il contesto per il thread specificato.  
  
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
 in Thread in esecuzione nel processo di destinazione.  
  
 `contextFlags`  
 in Specifica i flag di contesto. Corrisponde al campo ContextFlags del contesto. per ulteriori informazioni, vedere winnt. h, cercare CONTEXT_ALL.  
  
 `contextSize`  
 in Dimensioni del buffer specificato da pContext.  
  
 `pContext`  
 out Riceve la struttura del contesto specifica della piattaforma nel buffer specificato da pContext.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)