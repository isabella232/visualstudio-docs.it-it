---
description: Restituisce informazioni che consentono la costruzione di un messaggio di errore leggibile.
title: 'IDebugErrorEvent2:: GetErrorMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0ab15c0f232695dbc017d80f666154e5c35a8fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065775"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Restituisce informazioni che consentono la costruzione di un messaggio di errore leggibile.

## <a name="syntax"></a>Sintassi

```cpp
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

## <a name="parameters"></a>Parametri
`pMessageType`\
out Restituisce un valore dall'enumerazione [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , che descrive il tipo di messaggio.

`pbstrErrorFormat`\
out Il formato del messaggio finale per l'utente (vedere "osservazioni" per informazioni dettagliate).

`hrErrorReason`\
out Codice di errore relativo al messaggio.

`pdwType`\
out Gravità dell'errore (utilizzare le costanti MB_XXX per `MessageBox` , ad esempio, `MB_EXCLAMATION` o `MB_WARNING` ).

`pbstrHelpFileName`\
out Percorso di un file della guida (impostato su un valore null se non è presente alcun file della guida).

`pdwHelpId`\
out ID dell'argomento della guida da visualizzare (impostare su 0 se non è presente alcun argomento della guida).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il messaggio di errore deve essere formattato lungo le righe di `"What I was doing.  %1"` . Il `"%1"` verrebbe quindi sostituito dal chiamante con il messaggio di errore derivato dal codice di errore (restituito in `hrErrorReason` ). Il `pMessageType` parametro indica al chiamante il modo in cui deve essere visualizzato il messaggio di errore finale.

## <a name="see-also"></a>Vedi anche
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
