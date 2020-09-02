---
title: 'IEnumDebugProcesses2:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 931827891857d9a9f1364cd063b5fa30644257d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715908"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
Restituisce una copia dell'enumerazione corrente come oggetto separato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Clone(
   IEnumDebugProcesses2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugProcesses2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce una copia di questa enumerazione come oggetto separato.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 La copia dell'enumerazione ha lo stesso stato dell'originale al momento della chiamata di questo metodo. Tuttavia, gli Stati della copia e dell'originale sono separati e possono essere modificati singolarmente.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
