---
description: Sospende un thread.
title: 'IDebugThread2:: Suspend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 902418aeb18c149b0732e972a34ed89b56bb22ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081139"
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
out Restituisce il numero di Sospendi dopo l'operazione di sospensione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Ogni chiamata a questo metodo incrementa il conteggio di sospensione superiore a 0. Questo numero di Sospendi viene visualizzato nella finestra debug **thread** .

 Per ogni chiamata a questo metodo, deve essere presente una chiamata successiva al metodo [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Riprendi](../../../extensibility/debugger/reference/idebugthread2-resume.md)
