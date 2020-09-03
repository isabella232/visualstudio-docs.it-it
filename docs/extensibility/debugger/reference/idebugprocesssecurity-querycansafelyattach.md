---
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723205"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Questo metodo consente al fornitore della porta di visualizzare un avviso prima che l'utente si colleghi a un processo non sicuro.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valore restituito
 I valori restituiti sono i seguenti:

- `S_OK`: La connessione al processo è sicura e non viene visualizzata alcuna finestra di dialogo di avviso.

- `S_FALSE`: La connessione potrebbe essere un problema di sicurezza e viene visualizzata una finestra di dialogo con un avviso.

- `FAILURE`: La connessione al processo non riesce.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
