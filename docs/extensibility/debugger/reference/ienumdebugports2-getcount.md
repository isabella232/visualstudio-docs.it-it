---
title: IEnumDebugPorts2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::GetCount
helpviewer_keywords:
- IEnumDebugPorts2::GetCount
ms.assetid: d714455c-e4fc-48dc-a6d4-7e8b5d7c1bce
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8903e6634086a16462f7c8c285df7f9e56f21aff
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225650"
---
# <a name="ienumdebugports2getcount"></a>IEnumDebugPorts2::GetCount
Restituisce il numero di elementi nell'enumerazione.

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

 [out] Restituisce il numero di elementi nell'enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo non fa parte dell'interfaccia di enumerazione COM facoltativa che specifica che solo le `Next`, `Clone`, `Skip`, e `Reset` devono essere implementati i metodi.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)