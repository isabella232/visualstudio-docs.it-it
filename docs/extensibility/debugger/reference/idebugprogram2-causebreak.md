---
description: Richiede l'arresto dell'esecuzione del programma al successivo tentativo di esecuzione di uno dei relativi thread.
title: IDebugProgram2::CauseBreak | Microsoft Docs
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
ms.openlocfilehash: 7b97a95b1f4cfa4fa1451aab95b4d47a6a0e3eb3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057486"
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
 Un [evento IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) viene inviato quando il programma tenta di eseguire il codice dopo la chiamata a questo metodo.

 Questo metodo è asincrono in quanto il metodo restituisce immediatamente senza necessariamente attendere l'arresto del programma.

## <a name="see-also"></a>Vedi anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
