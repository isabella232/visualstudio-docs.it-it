---
description: Ottiene il GUID per questo processo.
title: IDebugProcess2::GetProcessId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca026ad8885056f4c05a57646207c2403058ccec0500430319f740ce6608f35a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338969"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Ottiene il GUID per questo processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Parametri
`pguidProcessId`\
[out] Restituisce il GUID per questo processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il GUID (Globally Unique IDentifier) identifica questo processo da tutti gli altri processi in esecuzione nel sistema.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
