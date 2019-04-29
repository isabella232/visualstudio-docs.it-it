---
title: 'Metodo ijsdebugprocess:: Createstackwalker | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateStackWalker
apilocation:
- jscript9diag.dll
ms.assetid: 9d02e21d-7900-4942-8d17-cd04a2261463
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb084b665467ae023bb885ee0de221f0409a0160
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557733"
---
# <a name="ijsdebugprocesscreatestackwalker-method"></a>Metodo IJsDebugProcess::CreateStackWalker
Metodo factory per chiamate nello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateStackWalker(  
   DWORD threadId,  
   IJsDebugStackWalker **ppStackWalker  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `threadId`  
 [in] ID del thread.  
  
 `ppStackWalker`  
 [out] Il nuovo oggetto percorso chiamate dello stack.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_JsDEBUG_UNKNOWN_THREAD se il thread non ha JavaScript su di esso. Questo metodo può essere chiamato solo durante il processo di destinazione è stato arrestato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)