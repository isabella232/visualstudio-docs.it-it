---
title: IDebugPort2::EnumProcesses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::EnumProcesses
helpviewer_keywords:
- IDebugPort2::EnumProcesses
ms.assetid: aafb32c5-5790-4807-a448-878a80256438
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c1b5b43007e43a5cee368622d808d20ad5b83b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343806"
---
# <a name="idebugport2enumprocesses"></a>IDebugPort2::EnumProcesses
Restituisce un elenco di tutti i processi in esecuzione su una porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT EnumProcesses( 
   IEnumDebugProcesses2** ppEnum
);
```

```csharp
int EnumProcesses( 
   out IEnumDebugProcesses2 ppEnum
);
```

## <a name="parameters"></a>Parametri
`ppEnum`\
[out] Restituisce un [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md) oggetto che contiene un elenco di tutti i processi in esecuzione su una porta.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)