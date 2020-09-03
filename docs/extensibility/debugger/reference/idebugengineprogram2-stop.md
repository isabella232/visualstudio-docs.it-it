---
title: 'IDebugEngineProgram2:: Stop | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 286a448ee33f57d2e3a3282dc8d72b11a843a9c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730478"
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

## <a name="remarks"></a>Osservazioni
 Questo metodo viene chiamato quando viene eseguito il debug di questo programma in un ambiente con più programmi. Quando viene ricevuto un evento di arresto da un altro programma, questo metodo viene chiamato su questo programma. L'implementazione di questo metodo deve essere asincrona. ovvero, non è necessario arrestare tutti i thread prima che questo metodo venga restituito. L'implementazione di questo metodo può essere semplice quanto la chiamata al metodo [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) su questo programma.

 Gli implementatori devono inviare un [IDebugStopCompleteEvent2](../../../extensibility/debugger/reference/idebugstopcompleteevent2.md) quando il programma si interrompe.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
