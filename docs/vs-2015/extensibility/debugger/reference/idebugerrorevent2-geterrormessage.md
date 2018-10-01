---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 516119fbe944b0aeeaa50516cf76a7745a5343f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530210"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugErrorEvent2::GetErrorMessage](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugerrorevent2-geterrormessage).  
  
Restituisce le informazioni che consentono la costruzione di un messaggio di errore leggibile dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
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

