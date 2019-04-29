---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84255e364630245564a0cbab5d38c6dff38df0a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978471"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Restituisce il risultato della valutazione dell'espressione come stringa e il valore restituito dell'operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `phrResult`  
 [out] Valore restituito dell'operazione.  
  
 `pbstrResult`  
 [out] Il risultato della valutazione dell'espressione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_PENDING`|L'operazione è ancora in sospeso.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce il risultato della valutazione dell'espressione come stringa e l'operazione `HRESULT`.  
  
 Questo metodo restituisce `S_OK` e `phrResult` restituisce `E_ABORT` se `Abort` interrompe l'operazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugExpression](../../winscript/reference/idebugexpression-interface.md)