---
title: 'Metodo ijsdebugbreakpoint:: Disable | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 873f5d285a877e04076859b0230589ced705078b
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348971"
---
# <a name="ijsdebugbreakpointdisable-method"></a>Metodo IJsDebugBreakPoint::Disable
Disabilita il punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="remarks"></a>Note  
 Restituisce E_UNEXPECTED se chiamato su un punto di interruzione eliminato. Restituisce S_FALSE se chiamato su un punto di interruzione già disabilitato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)