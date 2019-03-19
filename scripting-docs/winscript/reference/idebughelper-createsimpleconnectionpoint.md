---
title: IDebugHelper::CreateSimpleConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreateSimpleConnectionPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreateSimpleConnectionPoint
ms.assetid: 5e4798ce-6f9f-4184-9853-67bf8c8524ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f909a63f0f7ba70fca3c5e30e32a2d64c0147e9c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160433"
---
# <a name="idebughelpercreatesimpleconnectionpoint"></a>IDebugHelper::CreateSimpleConnectionPoint
Restituisce un'interfaccia di eventi che esegue il wrapping di un determinato `IDispatch` oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CreateSimpleConnectionPoint(  
   IDispatch*                pdisp  
   ISimpleConnectionPoint**  ppscp  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdisp`  
 [in] Il `IDispatch` oggetto per eseguire il wrapping.  
  
 `ppscp`  
 [out] L'interfaccia di eventi che esegue il wrapping `pdisp`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Restituisce un'interfaccia di eventi che esegue il wrapping di determinata `IDispatch` (vedere [interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)).  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Interfaccia ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)