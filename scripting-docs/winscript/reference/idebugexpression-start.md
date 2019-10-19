---
title: 'IDebugExpression:: Start | Microsoft Docs'
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
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576434"
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
 in Callback per indicare quando la valutazione dell'espressione è completa. Se questo parametro è `NULL`, non viene generato alcun evento e il client deve eseguire il polling dello stato dell'espressione utilizzando `QueryIsComplete`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo inizia la valutazione dell'espressione.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IDebugExpression:: Abort](../../winscript/reference/idebugexpression-abort.md)  
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)