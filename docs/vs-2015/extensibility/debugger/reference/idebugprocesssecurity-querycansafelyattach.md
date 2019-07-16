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
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187959"
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