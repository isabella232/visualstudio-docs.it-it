---
description: Ottiene il messaggio da visualizzare.
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d946a020e11b914cbb860c00d681bf94ca249dfaeed60a32b4d407c11f85a4d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433749"
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
[out] Restituisce un valore [dell'enumerazione MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) che descrive il tipo del messaggio.

`pbstrMessage`\
[out] Restituisce il messaggio.

`pdwType`\
[out] Restituisce il tipo del messaggio, usando le convenzioni della funzione `MessageBox` Win32. Per informazioni dettagliate, vedere la funzione [AfxMessageBox.](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

`pbstrHelpFileName`\
[in, out] Restituisce il nome del file della Guida. Può essere un valore Null (C++) o vuoto (C#) se non è presente alcun file della Guida.

`pdwHelpId`\
[in, out] Restituisce l'identificatore della Guida. Può essere 0 se al messaggio non è associata alcuna guida.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [Messagetype](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
