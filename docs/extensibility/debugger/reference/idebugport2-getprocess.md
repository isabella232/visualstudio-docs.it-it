---
description: Ottiene il processo specificato in esecuzione su una porta.
title: 'IDebugPort2:: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortSupplier
helpviewer_keywords:
- IDebugPort2::GetPortSupplier
ms.assetid: 3e2431b0-0e19-450d-8e1d-d7c314c8f872
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2ae7031a747ac31b2ec56b78de52dbc156973e5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087353"
---
# <a name="idebugport2getprocess"></a>IDebugPort2::GetProcess
Ottiene il processo specificato in esecuzione su una porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProcess( 
   AD_PROCESS_ID    ProcessId,
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess( 
   AD_PROCESS_ID      ProcessId,
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parametri
`ProcessId`\
in Struttura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) che specifica l'identificatore di processo.

`ppProcess`\
out Restituisce un oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
