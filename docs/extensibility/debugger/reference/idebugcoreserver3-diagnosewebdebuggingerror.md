---
description: Tenta di determinare il motivo per cui una connessione automatica non è riuscita.
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a7e41842842850f7eb9ff4993bba348aea9816f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077707"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Tenta di determinare il motivo per cui una connessione automatica non è riuscita.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametri
`pszUrl`\
in Non attualmente in uso; deve essere sempre impostato su un valore null.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Di seguito sono riportati altri codici restituiti tipici:

|Codice|Descrizione|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Impossibile determinare il motivo per cui il server remoto non è riuscito ad avviare il debug.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Impossibile eseguire il debug sul server remoto, probabilmente a causa di autorizzazioni insufficienti o perché il verbo di DEBUG non è abilitato.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Il server Web è stato bloccato e blocca il verbo di DEBUG, che è necessario per abilitare il debug.|

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
