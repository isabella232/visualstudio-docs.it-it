---
description: Recupera un elenco di tutti i thread in esecuzione nel processo.
title: IDebugProcess2::EnumThreads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ebb96bd93796b7320d5e41ef879ac723a197027
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050780"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Recupera un elenco di tutti i thread in esecuzione nel processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce un [oggetto IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) che contiene un elenco di tutti i thread in tutti i programmi nel processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo enumera i thread in esecuzione in ogni programma e li combina in una visualizzazione del processo dei thread. Un singolo thread può essere eseguito in più programmi. questo metodo enumera il thread una sola volta.

 Questo metodo presenta un elenco dei thread del processo senza duplicati. In caso contrario, per enumerare i thread in esecuzione in un programma specifico, usare il [metodo EnumThreads.](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
