---
title: 'Metodo ijsdebugbreakpoint:: IsEnabled | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b99df17f73896b4dd04481315b04e1672a56285a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583093"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>Metodo IJsDebugBreakPoint::IsEnabled
Determina se il punto di interruzione è abilitato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pIsEnabled`  
 [out] Restituisce true se il punto di interruzione è abilitato. in caso contrario, restituisce false.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_UNEXPECTED se chiamato su un punto di interruzione eliminato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)