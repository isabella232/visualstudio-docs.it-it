---
description: Tentativi di determinare il motivo per cui un collegamento automatico non è riuscito.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ec4af56afce3568577279fb1cefc09da0be22c974eb9acf1dd7d364e7c272d1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417522"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Tentativi di determinare il motivo per cui un collegamento automatico non è riuscito.

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
[in] Non attualmente in uso. deve essere sempre impostato su un valore Null.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Di seguito sono riportati altri codici restituiti tipici:

|Codice|Descrizione|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Impossibile determinare il motivo per cui il server remoto non è riuscito ad avviare il debug.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Impossibile eseguire il debug nel server remoto, probabilmente a causa di autorizzazioni insufficienti o perché il verbo DEBUG non è abilitato.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Il server Web è stato bloccato e blocca il verbo DEBUG, necessario per abilitare il debug.|

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
