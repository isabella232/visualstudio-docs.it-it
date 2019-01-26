---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70dc659fa1e3db2d4db797f3be82ba0239368f47
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069434"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Restituisce le informazioni che consentono la costruzione di un messaggio di errore leggibile dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pMessageType`  
 [out] Restituisce un valore di [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) enumerazione, che indica il tipo di messaggio.  
  
 `pbstrErrorFormat`  
 [out] Il formato del messaggio all'utente finale (per informazioni dettagliate, vedere "la sezione Osservazioni").  
  
 `hrErrorReason`  
 [out] Il codice di errore del messaggio è su.  
  
 `pdwType`  
 [out] Gravità dell'errore (usare le costanti MB_XXX `MessageBox`, ad esempio `MB_EXCLAMATION` o `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Percorso file della Guida (impostato su un valore null se non esiste alcun file della Guida).  
  
 `pdwHelpId`  
 [out] ID dell'argomento della Guida da visualizzare (impostato su 0 se non esiste alcun argomento della Guida).  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il messaggio di errore deve essere formattato lungo le righe di `"What I was doing.  %1"`. Il `"%1"` verrebbe quindi sostituita dal chiamante con il messaggio di errore derivato dal codice di errore (restituito nel `hrErrorReason`). Il `pMessageType` parametro indica al chiamante come deve essere visualizzato il messaggio di errore finale.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)