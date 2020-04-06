---
title: Proprietà IDebugEngineProgram2::WatchForThreadStep . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730348"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Gli orologi per l'esecuzione (o smette di controllare l'esecuzione) si verificano sul thread specificato.

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
[in] Oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) che rappresenta il programma sottoposto a un'istruzione stepd.

`dwTid`\
[in] Specifica l'identificatore del thread da controllare.

`fWatch`\
[in] Diverso da`TRUE`zero ( ) significa iniziare a `dwTid`guardare per l'esecuzione sul thread identificato da ; in caso`FALSE`contrario, zero ( `dwTid`) indica interrompere il controllo dell'esecuzione su .

`dwFrame`\
[in] Specifica un indice del frame che controlla il tipo di passaggio. Quando questo valore è zero (0), il tipo di passaggio è "step `dwTid` into" e il programma deve arrestarsi ogni volta che viene eseguito il thread identificato da. Quando `dwFrame` è diverso da zero, il tipo di passaggio è "step `dwTid` over" e il programma deve arrestarsi solo `dwFrame`se il thread identificato da è in esecuzione in un frame il cui indice è uguale o superiore nello stack di .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Quando il gestore di sessione di debug (SDM) esegue un'operazione di gestione di un programma, identificata dal `pOriginatingProgram` parametro , notifica tutti gli altri programmi collegati chiamando questo metodo.

 Questo metodo è applicabile solo all'esecuzione di istruzioni dello stesso thread.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
