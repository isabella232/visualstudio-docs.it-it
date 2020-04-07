---
title: IDebugErrorEvent2::GetErrorMessage ??? Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730039"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Restituisce informazioni che consentono la costruzione di un messaggio di errore leggibile.

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

## <a name="parameters"></a>Parametri
`pMessageType`\
[fuori] Restituisce un valore dall'enumerazione [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) che descrive il tipo di messaggio.

`pbstrErrorFormat`\
[fuori] Il formato del messaggio finale all'utente (vedere "Osservazioni" per i dettagli).

`hrErrorReason`\
[fuori] Il codice di errore di cui parla il messaggio.

`pdwType`\
[fuori] Gravità dell'errore (utilizzare le `MessageBox`costanti MB_XXX `MB_EXCLAMATION` per `MB_WARNING`; ad esempio, o ).

`pbstrHelpFileName`\
[fuori] Percorso di un file della Guida (impostato su un valore null se non è presente alcun file della Guida).

`pdwHelpId`\
[fuori] ID dell'argomento della Guida da visualizzare (impostare su 0 se non è presente alcun argomento della Guida).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Il messaggio di errore deve essere `"What I was doing.  %1"`formattato lungo le righe di . L'oggetto `"%1"` verrà quindi sostituito dal chiamante con il messaggio di `hrErrorReason`errore derivato dal codice di errore (restituito in ). Il `pMessageType` parametro indica al chiamante come deve essere visualizzato il messaggio di errore finale.

## <a name="see-also"></a>Vedere anche
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [Messagetype](../../../extensibility/debugger/reference/messagetype.md)
