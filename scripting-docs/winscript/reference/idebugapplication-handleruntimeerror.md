---
title: 'IDebugApplication:: HandleRuntimeError | Microsoft Docs'
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
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574326"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Determina il blocco del thread corrente e invia una notifica dell'errore all'IDE del debugger.  
  
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
 in Errore che si è verificato.  
  
 `pScriptSite`  
 in Sito di script del thread.  
  
 `pbra`  
 out Azione da intraprendere quando il debugger riprende l'applicazione.  
  
 `perra`  
 out Azione da intraprendere quando il debugger riprende l'applicazione se si verifica un errore.  
  
 `pfCallOnScriptError`  
 out Flag che è `TRUE` se il motore deve chiamare il metodo `IActiveScriptSite::OnScriptError`.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Un motore di linguaggio chiama questo metodo nel contesto di un thread che genera un errore di run-time. Questo metodo fa in modo che il thread corrente si blocchi e invii una notifica di errore da inviare all'IDE del debugger. Quando l'IDE del debugger riprende l'applicazione, questo metodo restituisce con l'azione da intraprendere.  
  
> [!NOTE]
> Durante l'errore di run-time, il motore del linguaggio può essere chiamato dal thread per eseguire attività quali l'enumerazione di stack frame o la valutazione delle espressioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md)    
 [Interfaccia IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)    
 @No__t_1 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)  
 @No__t_1 [enumerazione BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [Enumerazione ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)