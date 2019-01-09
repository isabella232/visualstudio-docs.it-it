---
title: IDebugApplication::HandleBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0478d0154ee79c1781885b94ae342e421e61e5e1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095368"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Fa sì che il thread corrente bloccare e invia una notifica del punto di interruzione per il debug dell'IDE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `br`  
 [in] Il motivo dell'interruzione.  
  
 `pbra`  
 [out] Azione da intraprendere quando il debugger consente di riprendere l'applicazione.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un motore del linguaggio chiama questo metodo nel contesto di un thread che raggiunge un punto di interruzione. Questo metodo blocca il thread corrente e invia una notifica di punto di interruzione per il debug dell'IDE. Quando il debugger consente di riprendere l'applicazione, il `pbra` parametro specifica l'azione da intraprendere.  
  
> [!NOTE]
>  Il motore del linguaggio può essere chiamato dal thread per eseguire le attività, ad esempio enumerare stack frame o valutano espressioni durante il punto di interruzione.  
  
 Questo metodo determina `IApplicationDebugger::onHandleBreakPoint` da chiamare.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Enumerazione BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)