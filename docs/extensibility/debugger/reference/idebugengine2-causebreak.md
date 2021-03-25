---
description: Richiede che tutti i programmi sottoposti a debug da questo motore di debug (DE) interrompano l'esecuzione la volta successiva che uno dei thread tenta di eseguire.
title: 'IDebugEngine2:: CauseBreak | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a320cbe9f2414de754b5844aa645bffb857568
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105093899"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Richiede che tutti i programmi sottoposti a debug da questo motore di debug (DE) interrompano l'esecuzione la volta successiva che uno dei thread tenta di eseguire.

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
 Questo metodo è asincrono: viene inviato un evento [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) quando il programma tenta di eseguire successiva dopo la chiamata a questo metodo.

## <a name="see-also"></a>Vedi anche
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
