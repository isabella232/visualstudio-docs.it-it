---
description: Restituisce il numero di elementi nell'enumerazione dei thread.
title: IEnumDebugThreads2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::GetCount
helpviewer_keywords:
- IEnumDebugThreads2::GetCount
ms.assetid: 81b7f139-d24e-4040-9adc-d664d77563ba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b7c37f0b69a3bd68c1328d37319968d19e68612
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636244"
---
# <a name="ienumdebugthreads2getcount"></a>IEnumDebugThreads2::GetCount
Restituisce il numero di elementi nell'enumerazione .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parametri
`pcelt`\
[out] Restituisce il numero di elementi nell'enumerazione .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo non fa parte dell'interfaccia di enumerazione COM personalizzata che specifica che devono essere implementati solo i metodi `Next` `Clone` , , e `Skip` `Reset` .

## <a name="see-also"></a>Vedi anche
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
