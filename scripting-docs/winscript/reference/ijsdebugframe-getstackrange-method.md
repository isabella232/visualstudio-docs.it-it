---
title: 'Metodo metodo ijsdebugframe:: GetStackRange | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574047"
---
# <a name="ijsdebugframegetstackrange-method"></a>Metodo IJsDebugFrame::GetStackRange
Restituisce l'intervallo di indirizzi assoluto della stack frame JavaScript logica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStart`  
 out Più basso puntatore dello stack del frame.  
  
 `pEnd`  
 out Più alto puntatore all'impilatore del frame.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Questo metodo è utile per riunire tracce dello stack Interleaved raccolte da più Runtime. I puntatori di stack iniziale, finale possono includere più stack frame del computer fisico (per i frame di runtime JavaScript interpretati). inizia > end Man mano che lo stack cresce dall'indirizzo alto a quello basso.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)