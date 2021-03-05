---
description: Esegue il programma del debugger.
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b3d996fd7b8cda1d5e36322c85d49c9889dd66dd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146002"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Esegue il programma del debugger. Il thread viene restituito per fornire al debugger le informazioni sul thread visualizzato dall'utente durante l'esecuzione del programma.

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
in Oggetto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un debugger può riprendere l'esecuzione dopo l'arresto in tre modi diversi:

- Execute: Annulla qualsiasi passaggio precedente e viene eseguito fino al punto di interruzione successivo e così via.

- Passaggio: annullare tutti i passaggi precedenti ed eseguire fino al completamento del nuovo passaggio.

- Continua: Esegui di nuovo e lascia attivo il passaggio precedente.

  Il thread passato a `ExecuteOnThread` è utile quando si decide quale passaggio annullare. Se non si conosce il thread, l'esecuzione di Execute Annulla tutti i passaggi. Con la conoscenza del thread, è sufficiente annullare il passaggio nel thread attivo.

## <a name="see-also"></a>Vedi anche
- [Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
