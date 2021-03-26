---
description: Restituisce un elenco di tutti i processi in esecuzione su una porta.
title: 'IDebugPort2:: EnumProcesses | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::EnumProcesses
helpviewer_keywords:
- IDebugPort2::EnumProcesses
ms.assetid: aafb32c5-5790-4807-a448-878a80256438
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d379b68ceaf5dfb36f2ce873c61eb4f52d98dff
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087548"
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
out Restituisce un oggetto [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md) che contiene un elenco di tutti i processi in esecuzione su una porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
