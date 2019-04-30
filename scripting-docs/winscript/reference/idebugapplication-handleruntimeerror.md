---
title: IDebugApplication::HandleRuntimeError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2c9a8b15b5095ac346ba047d6668aada7647a31
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412430"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Fa sì che il thread corrente bloccare e invia una notifica dell'errore per l'IDE di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pErrorDebug`  
 [in] Errore verificatosi.  
  
 `pScriptSite`  
 [in] Il sito dello script del thread.  
  
 `pbra`  
 [out] Azione da intraprendere quando il debugger consente di riprendere l'applicazione.  
  
 `perra`  
 [out] Azione da intraprendere quando il debugger consente di riprendere l'applicazione se si è verificato un errore.  
  
 `pfCallOnScriptError`  
 [out] Flag che è `TRUE` se il motore deve chiamare il `IActiveScriptSite::OnScriptError` (metodo).  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un motore del linguaggio chiama questo metodo nel contesto di un thread che comporta un errore di run-time. Questo metodo fa sì che il thread corrente bloccare e invia una notifica di errore da inviare al debugger di IDE. Quando l'IDE di debug viene ripresa l'applicazione, questo metodo restituisce con l'azione da intraprendere.  
  
> [!NOTE]
> Mentre nell'errore in fase di esecuzione, il motore del linguaggio può essere chiamato dal thread di eseguire tali attività come enumerare gli stack frame o valutare le espressioni.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugApplication Interface](../../winscript/reference/idebugapplication-interface.md)   
 [Interfaccia IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Enumerazione ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)