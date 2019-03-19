---
title: IApplicationDebugger::onHandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onHandleBreakPoint
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onHandleBreakPoint
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: edf8816cd646596ce1f897dfd9d949790d52b7b1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148217"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Gestisce l'evento punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `prpt`  
 [in] Il thread in cui si è verificato il punto di interruzione.  
  
 `br`  
 [in] Il motivo per il punto di interruzione.  
  
 `pError`  
 [in] Informazioni sugli errori di runtime, fornito quando il valore di `br` è BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato quando viene raggiunto un punto di interruzione e `IDebugApplication::HandleBreakPoint` viene chiamato.  
  
 L'applicazione rimarrà sospesa finché non viene chiamato l'IDE di debug `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)