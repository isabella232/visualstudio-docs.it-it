---
description: Riprende l'esecuzione di un thread.
title: 'IDebugThread2:: Resume | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93552bac60d16a21212bfa89816481cf7099d399
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053022"
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
out Restituisce il conteggio di sospensione dopo l'operazione di ripresa.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Ogni chiamata a questo metodo decrementa il conteggio di sospensione fino a quando non raggiunge 0, a quel punto, l'esecuzione viene ripresa. Questo numero di Sospendi viene visualizzato nella finestra debug **thread** .

 Per ogni chiamata a questo metodo, deve essere presente una chiamata precedente al metodo [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Il conteggio di sospensione determina il numero di volte in `IDebugThread2::Suspend` cui il metodo è stato chiamato finora.

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Sospendi](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
