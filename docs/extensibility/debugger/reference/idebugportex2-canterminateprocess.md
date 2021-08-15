---
description: Determina se un processo può essere terminato.
title: IDebugPortEx2::CanTerminateProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 814e0a0a5da0442f1127276c63b414cdb4ec0098968adbe41332a3868289bc58
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321922"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Determina se un processo può essere terminato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CanTerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
HRESULT CanTerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

## <a name="parameters"></a>Parametri
`pPortProcess`\
[in] Oggetto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) che rappresenta il processo da terminare.

## <a name="return-value"></a>Valore restituito
 Restituisce `S_OK` se il processo può essere terminato; in caso contrario, restituisce `S_FALSE` .

## <a name="see-also"></a>Vedi anche
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
