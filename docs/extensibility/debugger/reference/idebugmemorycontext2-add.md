---
description: Aggiunge il valore specificato al contesto corrente e restituisce un nuovo contesto.
title: IDebugMemoryContext2::Add | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d3926b151cc078dc879ebbe44ba3b902919bca3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127038"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Aggiunge il valore specificato al contesto corrente e restituisce un nuovo contesto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametri
`dwCount`\
[in] Valore da aggiungere al contesto corrente.

`ppMemCxt`\
[out] Restituisce un nuovo [oggetto IDebugMemoryContext2.](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Un contesto di memoria è un indirizzo, pertanto l'aggiunta di un valore a un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia di contesto.

 Questo metodo deve sempre produrre un nuovo contesto, anche se l'indirizzo risultante non è compreso nello spazio di memoria associato a questo contesto. L'unica eccezione è se non è possibile allocare memoria per il nuovo contesto o se è `ppMemCxt` un valore Null (che è un errore).

## <a name="see-also"></a>Vedi anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
