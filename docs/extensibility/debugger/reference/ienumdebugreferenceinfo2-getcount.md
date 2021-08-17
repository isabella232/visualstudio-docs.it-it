---
description: Restituisce il numero di DEBUG_REFERENCE_INFO nell'enumerazione .
title: IEnumDebugReferenceInfo2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::GetCount
helpviewer_keywords:
- IEnumDebugReferenceInfo2::GetCount
ms.assetid: e62706e0-d2cd-48fb-8fdf-444463c651ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 045bdf53bd131a970dd17811dbf43b7d1b5589a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125439"
---
# <a name="ienumdebugreferenceinfo2getcount"></a>IEnumDebugReferenceInfo2::GetCount
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
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
