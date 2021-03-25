---
description: Questo metodo consente al fornitore della porta di visualizzare un avviso prima che l'utente si colleghi a un processo non sicuro.
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cbbfcf11a35fcfc43ae9e903b13a7480a3cf9743
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076277"
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

## <a name="see-also"></a>Vedi anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
