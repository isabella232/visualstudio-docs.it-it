---
title: IDebugThread2::GetThreadId . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7788cc09d92ff4c784fbcb7004393fe0d3074c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718699"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Ottiene l'identificatore del thread di sistema.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>Parametri
`pdwThreadId`\
[fuori] Restituisce l'identificatore del thread di sistema.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Un ID thread viene utilizzato per identificare un thread tra tutti gli altri thread di un processo.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come `CProgram` implementare questo metodo per un oggetto semplice che implementa il [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interfaccia.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
