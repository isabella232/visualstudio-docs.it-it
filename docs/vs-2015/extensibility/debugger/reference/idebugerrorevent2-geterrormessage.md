---
title: 'IDebugErrorEvent2:: GetErrorMessage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4b25e040fe391b0bfbd05159779096e6bad9951
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183512"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce informazioni che consentono la costruzione di un messaggio di errore leggibile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 out Restituisce un valore dall'enumerazione [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , che descrive il tipo di messaggio.  
  
 `pbstrErrorFormat`  
 out Il formato del messaggio finale per l'utente (vedere "osservazioni" per informazioni dettagliate).  
  
 `hrErrorReason`  
 out Codice di errore relativo al messaggio.  
  
 `pdwType`  
 out Gravità dell'errore (utilizzare le costanti MB_XXX per `MessageBox` , ad esempio, `MB_EXCLAMATION` o `MB_WARNING` ).  
  
 `pbstrHelpFileName`  
 out Percorso di un file della guida (impostato su un valore null se non è presente alcun file della guida).  
  
 `pdwHelpId`  
 out ID dell'argomento della guida da visualizzare (impostare su 0 se non è presente alcun argomento della guida).  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 Il messaggio di errore deve essere formattato lungo le righe di `"What I was doing.  %1"` . Il `"%1"` verrebbe quindi sostituito dal chiamante con il messaggio di errore derivato dal codice di errore (restituito in `hrErrorReason` ). Il `pMessageType` parametro indica al chiamante il modo in cui deve essere visualizzato il messaggio di errore finale.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
