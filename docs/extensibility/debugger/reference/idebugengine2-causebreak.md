---
description: Richiede a tutti i programmi di cui viene eseguito il debug da questo motore di debug (DE) di arrestare l'esecuzione al successivo tentativo di esecuzione di uno dei thread.
title: IDebugEngine2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed068e3f0a5e1a595b9f93fec5d19de8b30690fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711950"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Richiede a tutti i programmi di cui viene eseguito il debug da questo motore di debug (DE) di arrestare l'esecuzione al successivo tentativo di esecuzione di uno dei thread.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CauseBreak( 
   void 
);
```

```csharp
int CauseBreak();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo è asincrono: un [evento IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) viene inviato al successivo tentativo di esecuzione del programma dopo la chiamata di questo metodo.

## <a name="see-also"></a>Vedi anche
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
