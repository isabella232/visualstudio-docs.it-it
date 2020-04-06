---
title: IDebugProcessSecurity::QueryCanSafelyAttach Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723205"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Questo metodo consente al fornitore della porta di visualizzare un avviso prima che l'utente si connette a un processo non sicuro.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valore restituito
 I valori restituiti sono i seguenti:

- `S_OK`: la connessione al processo è sicura e non viene visualizzata alcuna finestra di dialogo di avviso.

- `S_FALSE`: il collegamento potrebbe essere un problema di sicurezza e viene visualizzata una finestra di dialogo con un avviso.

- `FAILURE`: collegamento al processo non riuscito.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
