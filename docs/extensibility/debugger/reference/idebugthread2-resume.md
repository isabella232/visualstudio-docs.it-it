---
description: Riprende l'esecuzione di un thread.
title: IDebugThread2::Resume | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d40acc8c70c34cecbd05506af57a9b784da08c91
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126068"
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
[out] Restituisce il conteggio di sospensione dopo l'operazione di ripresa.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Ogni chiamata a questo metodo decrementa il conteggio delle sospenszioni fino a raggiungere 0 nel momento in cui l'esecuzione viene effettivamente ripresa. Questo conteggio di sospensione viene visualizzato nella finestra **di** debug Thread.

 Per ogni chiamata a questo metodo, deve essere presente una chiamata precedente al [metodo Suspend.](../../../extensibility/debugger/reference/idebugthread2-suspend.md) Il conteggio di sospensione determina quante volte `IDebugThread2::Suspend` il metodo è stato chiamato finora.

## <a name="see-also"></a>Vedi anche
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Sospendi](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
