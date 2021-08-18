---
description: Recupera l'ID del processo proprietario dell'oggetto rappresentato da questa interfaccia IDebugAddress2.
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35139838a879aa742ded8d3aac2b57cd71500821
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122064890"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Recupera l'ID del processo proprietario dell'oggetto rappresentato da questa [interfaccia IDebugAddress2.](../../../extensibility/debugger/reference/idebugaddress2.md)

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>Parametri
`pProcID`\
[out] ID del processo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
