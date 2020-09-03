---
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722653"
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

## <a name="remarks"></a>Osservazioni
 Un debugger può riprendere l'esecuzione dopo l'arresto in tre modi diversi:

- Execute: Annulla qualsiasi passaggio precedente e viene eseguito fino al punto di interruzione successivo e così via.

- Passaggio: annullare tutti i passaggi precedenti ed eseguire fino al completamento del nuovo passaggio.

- Continua: Esegui di nuovo e lascia attivo il passaggio precedente.

  Il thread passato a `ExecuteOnThread` è utile quando si decide quale passaggio annullare. Se non si conosce il thread, l'esecuzione di Execute Annulla tutti i passaggi. Con la conoscenza del thread, è sufficiente annullare il passaggio nel thread attivo.

## <a name="see-also"></a>Vedere anche
- [Eseguire](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
