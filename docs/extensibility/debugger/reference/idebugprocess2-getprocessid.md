---
title: IDebugProcess2::GetProcessId . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 12e575979e5bd1527dfa0d8e15b290d6b78e36ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723899"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Ottiene il GUID per questo processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Parametri
`pguidProcessId`\
[fuori] Restituisce il GUID per questo processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 L'identificatore univoco globale (GUID, Globally Unique IDentifier) identifica questo processo da tutti gli altri processi in esecuzione nel sistema.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
