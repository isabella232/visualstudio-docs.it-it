---
title: 'Metodo ijsdebugframe:: GetStackRange | Microsoft Docs'
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
ms.openlocfilehash: 52dd6114d3ec462f91f8bce5e76f73c5487746ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558216"
---
# <a name="ijsdebugframegetstackrange-method"></a>Metodo IJsDebugFrame::GetStackRange
Restituisce l'intervallo di indirizzi assoluti dello stack frame JavaScript logico.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pStart`  
 [out] Bottom la maggior parte dei puntatori agli stack del frame.  
  
 `pEnd`  
 [out] Primi la maggior parte delle puntatore di impilatore del frame.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Questo metodo è utile per riunire tracce dello stack con interfoliazione raccolte da più runtime. Inizio, fine dello stack puntatori possono includere più frame dello stack di computer fisico (per i frame di runtime JavaScript interpretati). Start > Fine man mano che aumenta lo stack dall'alto in basso indirizzo.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)