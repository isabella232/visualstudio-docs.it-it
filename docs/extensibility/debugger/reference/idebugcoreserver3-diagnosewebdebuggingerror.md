---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63d6bce43062996ae14c704908543b86adce2877
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66205550"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Per determinare il motivo per cui un auto-attach tentativi non riusciti.

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
[in] Attualmente non usato; deve sempre essere impostata su un valore null.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Di seguito sono indicati altri codici restituiti tipici:

|Codice|Descrizione|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Non è possibile determinare il motivo per cui il server remoto non è stato possibile avviare il debug.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Impossibile eseguire il debug sul server remoto, probabilmente a causa di autorizzazioni insufficienti o perché il verbo DEBUG non è abilitato.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Il server web è stato bloccato e blocca il verbo DEBUG, che è necessario abilitare il debug.|

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)