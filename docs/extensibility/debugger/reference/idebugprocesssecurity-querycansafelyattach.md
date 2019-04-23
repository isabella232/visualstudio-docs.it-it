---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 891a0c200b02f8768ef68d1d87649bfd35cf59d2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040611"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Questo metodo consente il fornitore della porta visualizzare un avviso prima che l'utente si connette a un processo non sicuro.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Valore restituito
 I valori restituiti sono come segue:

- `S_OK`: La connessione al processo è sicura e non viene visualizzata alcuna finestra di dialogo di avviso.

- `S_FALSE`: La connessione potrebbe essere un problema di sicurezza e viene visualizzata una finestra di dialogo con un avviso.

- `FAILURE`: La connessione al processo avrà esito negativo.

## <a name="see-also"></a>Vedere anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)