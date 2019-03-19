---
title: IDebugExpression::Start | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e80f3fb8087d39c76f59cf5c6bc8719c1cbaf5e4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145044"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Inizia la valutazione dell'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdecb`  
 [in] Callback per indicare quando viene completata la valutazione dell'espressione. Se questo parametro è `NULL`, viene generato alcun evento e il client deve eseguire il polling dello stato di espressione usando `QueryIsComplete`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo avvia la valutazione dell'espressione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)