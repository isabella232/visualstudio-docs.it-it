---
title: 'IDebugProcess2:: EnumThreads | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52383649fc45eae6bbac6831f9bb233b9c0a2fde
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724060"
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
out Restituisce un oggetto [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) che contiene un elenco di tutti i thread in tutti i programmi nel processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo enumera i thread in esecuzione in ogni programma e li combina in una visualizzazione processo dei thread. Un thread singolo può essere eseguito in più programmi; Questo metodo enumera il thread una sola volta.

 Questo metodo presenta un elenco dei thread del processo senza duplicati. In caso contrario, per enumerare i thread in esecuzione in un particolare programma, utilizzare il metodo [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) .

## <a name="see-also"></a>Vedere anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
