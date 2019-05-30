---
title: IDebugProcess2::EnumThreads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 664f4264fd12106fef0650a31a888470e09a3154
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353177"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
Recupera un elenco di tutti i thread in esecuzione nel processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce un [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) oggetto che contiene un elenco di tutti i thread in tutti i programmi nel processo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo enumera i thread in esecuzione in ciascun programma e quindi le combina in una vista di processo dei thread. Un singolo thread possono essere eseguite in più programmi; Questo metodo enumera solo una volta tale thread.

 Questo metodo presenta un elenco di thread del processo senza duplicati. In caso contrario, per enumerare i thread in esecuzione in un particolare programma, usare il [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)