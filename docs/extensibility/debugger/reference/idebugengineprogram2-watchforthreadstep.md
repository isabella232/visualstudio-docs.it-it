---
description: Controlla l'esecuzione (o interrompe il controllo dell'esecuzione) nel thread specificato.
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6acb6dfe32adba3dccd30e38e2bb3b18d4dc5d2c190a966c05beb34df7395a3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121389995"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Controlla l'esecuzione (o interrompe il controllo dell'esecuzione) nel thread specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>Parametri
`pOriginatingProgram`\
[in] Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma in fase di esecuzione.

`dwTid`\
[in] Specifica l'identificatore del thread da controllare.

`fWatch`\
[in] Diverso da zero ( ) significa avviare il controllo dell'esecuzione sul thread identificato da ; in caso contrario, zero ( ) significa interrompere il controllo `TRUE` `dwTid` `FALSE` dell'esecuzione in `dwTid` .

`dwFrame`\
[in] Specifica un indice di frame che controlla il tipo di passaggio. Quando il valore è zero (0), il tipo di passaggio è "esegui istruzione" e il programma deve arrestarsi ogni volta che viene eseguito il thread `dwTid` identificato da . Quando è diverso da zero, il tipo di passaggio è "step over" e il programma deve essere interrotta solo se il thread identificato da è in esecuzione in un frame il cui indice è uguale o superiore nello stack rispetto `dwFrame` `dwTid` a `dwFrame` .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Quando gestione debug sessione (SDM) esegue il debug di un programma, identificato dal parametro , invia una notifica a tutti gli altri programmi collegati `pOriginatingProgram` chiamando questo metodo.

 Questo metodo è applicabile solo all'esecuzione di istruzioni dello stesso thread.

## <a name="see-also"></a>Vedi anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
