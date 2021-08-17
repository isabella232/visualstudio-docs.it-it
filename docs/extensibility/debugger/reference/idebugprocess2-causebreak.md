---
description: Richiede che il programma successivo che esegue il codice in questo processo si interrompi e invii un oggetto evento IDebugBreakEvent2.
title: IDebugProcess2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2ec4939575e1c31ccbc5114ec3c3676d34a7c74e0b0510cd80218df97211e5e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121416488"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
Richiede che il programma successivo che esegue il codice in questo processo si interrompi e invii un oggetto evento [IDebugBreakEvent2.](../../../extensibility/debugger/reference/idebugbreakevent2.md)

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

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
