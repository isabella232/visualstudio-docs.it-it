---
description: Arresta tutti i thread in esecuzione in questo programma.
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 64aa3bf0b8281e58e867b08a92460054255ca698
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127233"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Arresta tutti i thread in esecuzione in questo programma.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Stop( 
   void 
);
```

```csharp
int Stop();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato quando il programma è in fase di debug in un ambiente a più programmi. Quando viene ricevuto un evento di arresto da un altro programma, questo metodo viene chiamato su questo programma. L'implementazione di questo metodo deve essere asincrona. ciò significa che non è necessario che tutti i thread siano arrestati prima che il metodo venga restituito. L'implementazione di questo metodo può essere semplice quanto chiamare il [metodo CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) in questo programma.

 Gli implementatori devono inviare [un oggetto IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) all'arresto del programma.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
