---
title: 'IDebugApplication:: HandleBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30937817424e88f80cfa6afa8c874adfd2b2687b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574968"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Fa in modo che il thread corrente si blocchi e invii una notifica del punto di interruzione all'IDE del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `br`  
 in Motivo dell'interruzioni.  
  
 `pbra`  
 out Azione da intraprendere quando il debugger riprende l'applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un motore di linguaggio chiama questo metodo nel contesto di un thread che raggiunge un punto di interruzione. Questo metodo blocca il thread corrente e invia una notifica del punto di interruzione all'IDE del debugger. Quando il debugger riprende l'applicazione, il `pbra` parametro specifica l'azione da intraprendere.  
  
> [!NOTE]
> Il modulo di gestione del linguaggio può essere chiamato dal thread per eseguire attività quali l'enumerazione di stack frame o la valutazione di espressioni durante il punto di interruzione.  
  
 Questo metodo fa sì che `IApplicationDebugger::onHandleBreakPoint` venga chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)    
 @No__t_1 [IApplicationDebugger:: onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)  
 @No__t_1 [enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)  
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)