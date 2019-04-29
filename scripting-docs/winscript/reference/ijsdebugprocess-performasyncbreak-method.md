---
title: 'Metodo ijsdebugprocess:: Performasyncbreak | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.PerformAsyncBreak
apilocation:
- jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a4fdb70341744c764779d406372bbd55418fd29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557985"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>Metodo IJsDebugProcess::PerformAsyncBreak
Inserisce il motore di script in modalità di interruzione facendo in modo che in modo da interrompere successiva istruzione di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `threadId`  
 [in] ID del thread.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)