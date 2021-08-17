---
description: Restituisce informazioni che consentono la costruzione di un messaggio di errore leggibile dall'utente.
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c35d0bda87ded6de95b7bc744c01ea82a97ab3354a2dbf0330dd2abcd18a5097
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417314"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Restituisce informazioni che consentono la costruzione di un messaggio di errore leggibile dall'utente.

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
[out] Restituisce un valore [dall'enumerazione MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) che descrive il tipo di messaggio.

`pbstrErrorFormat`\
[out] Formato del messaggio finale per l'utente (per informazioni dettagliate, vedere "Osservazioni").

`hrErrorReason`\
[out] Codice di errore di cui si tratta il messaggio.

`pdwType`\
[out] Gravità dell'errore (usare le costanti MB_XXX per `MessageBox` , ad esempio o `MB_EXCLAMATION` `MB_WARNING` ).

`pbstrHelpFileName`\
[out] Percorso di un file della Guida (impostato su un valore Null se non è presente alcun file della Guida).

`pdwHelpId`\
[out] ID dell'argomento della Guida da visualizzare (impostato su 0 se non è presente alcun argomento della Guida).

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il messaggio di errore deve essere formattato in base alle righe di `"What I was doing.  %1"` . Verrà `"%1"` quindi sostituito dal chiamante con il messaggio di errore derivato dal codice di errore (restituito in `hrErrorReason` ). Il parametro indica al chiamante come deve essere visualizzato il `pMessageType` messaggio di errore finale.

## <a name="see-also"></a>Vedi anche
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [Messagetype](../../../extensibility/debugger/reference/messagetype.md)
