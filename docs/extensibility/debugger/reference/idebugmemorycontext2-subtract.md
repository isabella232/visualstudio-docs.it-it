---
title: 'IDebugMemoryContext2:: Subtract | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727444"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Sottrae il valore specificato dal contesto corrente e restituisce un nuovo contesto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametri
`dwCount`\
in Numero di byte di memoria da decrementare.

`ppMemCxt`\
out Restituisce un nuovo oggetto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Un contesto di memoria è un indirizzo, quindi la sottrazione di un valore da un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia di contesto.

 Questo metodo deve sempre produrre un nuovo contesto, anche se l'indirizzo risultante è esterno allo spazio di memoria associato a questo contesto. L'unica eccezione è rappresentata dal caso in cui non sia possibile allocare memoria per il nuovo contesto o se `ppMemCxt` è un valore null (errore).

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
