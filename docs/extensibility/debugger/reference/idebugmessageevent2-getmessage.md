---
title: Proprietà IDebugMessageEvent2::GetMessage . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 819b796a656f0ef8775fbb1c9e800e3019b81729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727406"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Ottiene il messaggio da visualizzare.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>Parametri
`pMessageType`\
[fuori] Restituisce un valore dall'enumerazione [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) che descrive il tipo del messaggio.

`pbstrMessage`\
[fuori] Restituisce il messaggio.

`pdwType`\
[fuori] Restituisce il tipo del messaggio, utilizzando le `MessageBox` convenzioni della funzione Win32. Vedere la funzione [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) per i dettagli.

`pbstrHelpFileName`\
[in, out] Restituisce il nome del file della Guida. Può essere un valore null (C) o vuoto (C) se non è presente alcun file della Guida.

`pdwHelpId`\
[in, out] Restituisce l'identificatore della Guida. Può essere 0 se non vi è alcuna Guida associata a questo messaggio.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedere anche
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [Messagetype](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
