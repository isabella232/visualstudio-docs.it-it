---
description: Restituisce il numero di elementi nell'enumerazione dei programmi.
title: IEnumDebugPrograms2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::GetCount
helpviewer_keywords:
- IEnumDebugPrograms2::GetCount
ms.assetid: 84832982-fa68-4090-a5b7-b233817876b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: affb506f81acc20aec2bac35940fa572be7fd4be52d376d6e0b9037c4a98a059
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360066"
---
# <a name="ienumdebugprograms2getcount"></a>IEnumDebugPrograms2::GetCount
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
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
