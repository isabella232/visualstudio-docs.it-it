---
title: 'Metodo ijsdebugstackwalker:: GetNext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugStackWalker.GetNext
apilocation:
- jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba8931a01f3afe05f791f4d89da60a9354868215
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148451"
---
# <a name="ijsdebugstackwalkergetnext-method"></a>Metodo IJsDebugStackWalker::GetNext
Ottiene il frame successivo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppFrame`  
 [out] Oggetto che rappresenta il frame dello stack.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_JsDEBUG_OUTSIDE_OF_VM quando non sono più stack frame da enumerare  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugStackWalker](../../winscript/reference/ijsdebugstackwalker-interface.md)