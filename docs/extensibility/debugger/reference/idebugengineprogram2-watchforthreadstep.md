---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6b3f8db95d6e74a2aa1d146bdd37a66803a8503f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345151"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Controlla che l'esecuzione viene arrestata la visione per l'esecuzione (o) venga eseguita il thread specificato.

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
[in] Un' [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto che rappresenta il programma in corso rientri.

`dwTid`\
[in] Specifica l'identificatore del thread da controllare.

`fWatch`\
[in] Diverso da zero (`TRUE`) significa che inizia a guardare per l'esecuzione sul thread identificato da `dwTid`; in caso contrario, zero (`FALSE`) significa interruzione il controllo per l'esecuzione su `dwTid`.

`dwFrame`\
[in] Specifica un indice dei fotogrammi che controlla il tipo di passaggio. Quando si tratta di valore è zero (0), il tipo di passaggio è "eseguire l'istruzione" e il programma deve essere arrestata ogni volta che il thread identificato da `dwTid` esegue. Quando `dwFrame` è diverso da zero, il tipo di passaggio è "Esegui istruzione/routine" e il programma deve essere interrotta solo se il thread identificato da `dwTid` è in esecuzione in un frame di cui indice è uguale o superiore nello stack di `dwFrame`.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Quando i passaggi da un programma, identificato dal gestore di sessione di debug (SDM) il `pOriginatingProgram` parametro, notifica a tutti gli altri programmi collegati chiamando questo metodo.

 Questo metodo è applicabile solo per l'esecuzione di istruzioni stesso thread.

## <a name="see-also"></a>Vedere anche
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)