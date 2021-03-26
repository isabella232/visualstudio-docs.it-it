---
description: Ottiene una descrizione del processo.
title: 'IDebugProcess2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01771f011df4e40b2323ef9cc44027f9456c2fbf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081841"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Ottiene una descrizione del processo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Parametri
`Fields`\
in Combinazione di valori dell'enumerazione [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) che specifica i campi del `pProcessInfo` parametro da compilare.

`pProcessInfo`\
out Struttura [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) compilata con una descrizione del processo.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
