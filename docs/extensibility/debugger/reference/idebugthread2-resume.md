---
title: IDebugThread2::Riprendi . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718681"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Riprende l'esecuzione di un thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametri
`pdwSuspendCount`\
[fuori] Restituisce il conteggio delle sospensioni dopo l'operazione di ripresa.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Ogni chiamata a questo metodo decrementa il conteggio delle sospensioni fino a raggiungere 0 al momento in cui l'esecuzione viene effettivamente ripresa. Questo conteggio delle sospensioni viene visualizzato nella finestra di debug **Thread.This** suspend count is displayed in the Threads debug window.

 Per ogni chiamata a questo metodo, deve essere presente una chiamata precedente al [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) metodo. Il conteggio delle sospensioni `IDebugThread2::Suspend` determina quante volte il metodo è stato chiamato finora.

## <a name="see-also"></a>Vedere anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Sospendere](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
