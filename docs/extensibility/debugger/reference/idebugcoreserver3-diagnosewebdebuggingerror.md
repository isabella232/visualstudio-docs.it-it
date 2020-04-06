---
title: IDebugCoreServer3::DiagnoseWebDebuggingError . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fec5b8fbe1cae18b8221702fe14443df231d8880
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732956"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Tenta di determinare il motivo per cui un collegamento automatico non è riuscito.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parametri
`pszUrl`\
[in] Non attualmente utilizzato; deve essere sempre impostato su un valore null.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Di seguito sono riportati altri codici restituiti tipici:

|Codice|Descrizione|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Impossibile determinare il motivo per cui il server remoto non è riuscito ad avviare il debug.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Impossibile eseguire il debug sul server remoto, probabilmente a causa di autorizzazioni insufficienti o perché il verbo DEBUG non è abilitato.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Il server Web è stato bloccato e sta bloccando il verbo DEBUG, necessario per abilitare il debug.|

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
