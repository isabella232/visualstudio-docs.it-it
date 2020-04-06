---
title: Proprietà IDebugProgram3::ExecuteOnThread . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722653"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Esegue il programma debugger. Il thread viene restituito per fornire al debugger informazioni su quale thread l'utente sta visualizzando durante l'esecuzione del programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parametri
`pThread`\
[in] Oggetto [IDebugThread2.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Esistono tre modi diversi in cui un debugger può riprendere l'esecuzione dopo l'arresto:There are three different ways that a debugger can resume execution after stopping:

- Esegui: consente di annullare qualsiasi passaggio precedente ed eseguire fino al punto di interruzione successivo e così via.

- Passaggio: Annullare qualsiasi passaggio precedente ed eseguilo fino al completamento del nuovo passaggio.

- Continua: eseguire di nuovo e lasciare attivo qualsiasi passaggio precedente.

  Il thread `ExecuteOnThread` passato a è utile per decidere quale passaggio annullare. Se non si conosce il thread, l'esecuzione di execute annulla tutti i passaggi. Con la conoscenza del thread, è sufficiente annullare il passaggio sul thread attivo.

## <a name="see-also"></a>Vedere anche
- [Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
