---
description: Richiede l'arresto dell'esecuzione del programma al successivo tentativo di esecuzione di uno dei relativi thread.
title: Interfaccia IDebugProgram2::CauseBreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6998321eb31c97fc2751d0ea50f49d7fbb73a9347ef0403d545ea285a6c40f5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433372"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Richiede l'arresto dell'esecuzione del programma al successivo tentativo di esecuzione di uno dei relativi thread.

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
 Un [evento IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) viene inviato quando il programma tenta di eseguire il codice dopo la chiamata di questo metodo.

 Questo metodo è asincrono in quanto il metodo restituisce immediatamente un risultato senza attendere necessariamente l'arresto del programma.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
