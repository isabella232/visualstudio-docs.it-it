---
title: IRemoteDebugApplicationEvents::OnEnterBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnEnterBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnEnterBreakPoint
ms.assetid: e92a56a3-c462-4a76-8ae8-4b2e6836a711
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 123476100076811534343763f0e9675a90fdea16
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934651"
---
# <a name="iremotedebugapplicationeventsonenterbreakpoint"></a>IRemoteDebugApplicationEvents::OnEnterBreakPoint
Gestisce un evento per l'immissione di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT OnEnterBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `prdat`  
 [in] Il thread dell'applicazione che accede al punto di interruzione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo gestisce un evento per l'immissione di un punto di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)