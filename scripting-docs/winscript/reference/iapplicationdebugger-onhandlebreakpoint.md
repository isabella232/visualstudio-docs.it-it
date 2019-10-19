---
title: 'IApplicationDebugger:: onHandleBreakPoint | Microsoft Docs'
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
ms.openlocfilehash: 3796ea1f50f0c4bcf945dbc10592c048db22757b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577836"
---
# <a name="iapplicationdebuggeronhandlebreakpoint"></a>IApplicationDebugger::onHandleBreakPoint
Gestisce un evento del punto di interruzione.  
  
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
 in Thread in cui si è verificato il punto di interruzione.  
  
 `br`  
 in Motivo del punto di interruzione.  
  
 `pError`  
 in Informazioni sugli errori di runtime, fornite quando il valore di `br` è BREAKREASON_ERROR.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato quando viene raggiunto un punto di interruzione e viene chiamato `IDebugApplication::HandleBreakPoint`.  
  
 L'applicazione resterà sospesa finché l'IDE del debugger non chiamerà `IRemoteDebugApplication::ResumeFromBreakPoint`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)    
 @No__t_1 [IDebugApplication:: HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)  
 @No__t_1 [IRemoteDebugApplication:: ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)  
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)