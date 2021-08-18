---
description: Esegue il programma del debugger.
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0e903431dbdcc4853d205ea6107ca6e70b91647
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126518"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Esegue il programma del debugger. Il thread viene restituito per fornire al debugger informazioni sul thread visualizzato dall'utente durante l'esecuzione del programma.

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

## <a name="remarks"></a>Commenti
 Esistono tre modi diversi in cui un debugger può riprendere l'esecuzione dopo l'arresto:

- Esegui: annullare qualsiasi passaggio precedente ed eseguire fino al punto di interruzione successivo e così via.

- Passaggio: annullare qualsiasi passaggio precedente ed eseguire fino al completamento del nuovo passaggio.

- Continua: eseguire di nuovo e lasciare attivo qualsiasi passaggio precedente.

  Il thread passato a `ExecuteOnThread` è utile quando si decide quale passaggio annullare. Se non si conosce il thread, l'esecuzione dell'esecuzione annulla tutti i passaggi. Con la conoscenza del thread, è necessario annullare solo il passaggio nel thread attivo.

## <a name="see-also"></a>Vedi anche
- [Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
