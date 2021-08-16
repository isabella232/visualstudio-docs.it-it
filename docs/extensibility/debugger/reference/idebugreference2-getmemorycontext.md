---
description: Ottiene un contesto di memoria di un riferimento.
title: IDebugReference2::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryContext
helpviewer_keywords:
- IDebugReference2::GetMemoryContext
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7148be6288df7a494d64732a73d52281d622a0b761794cd2c0c55ae370e89de8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338592"
---
# <a name="idebugreference2getmemorycontext"></a>IDebugReference2::GetMemoryContext
Ottiene un contesto di memoria di un riferimento. Riservato per utilizzi futuri.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext ( 
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>Parametri
`ppMemory`\
[out] Restituisce [l'oggetto IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) che rappresenta la memoria associata al valore del riferimento.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL`.

## <a name="see-also"></a>Vedi anche
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
