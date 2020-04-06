---
title: IDebugThread2::Suspend . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718634"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Sospende un thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametri
`pdwSuspendCount`\
[fuori] Restituisce il conteggio delle sospensioni dopo l'operazione di sospensione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Ogni chiamata a questo metodo incrementa il conteggio delle sospensioni superiore a 0.Each call to this method increments the suspend count above 0. Questo conteggio delle sospensioni viene visualizzato nella finestra di debug **Thread.This** suspend count is displayed in the Threads debug window.

 Per ogni chiamata a questo metodo, deve essere presente una chiamata successiva al [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
