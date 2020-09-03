---
title: 'IDebugProgram2:: CauseBreak | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e96db32d7ba5a01f89530623c949500a265cdb60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723106"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Richiede l'arresto dell'esecuzione del programma la volta successiva che uno dei thread tenta di eseguire.

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

## <a name="remarks"></a>Osservazioni
 Un evento [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) viene inviato quando il programma tenta di eseguire il codice dopo la chiamata a questo metodo.

 Questo metodo è asincrono perché il metodo restituisce immediatamente un risultato senza necessariamente attendere l'arresto del programma.

## <a name="see-also"></a>Vedere anche
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
