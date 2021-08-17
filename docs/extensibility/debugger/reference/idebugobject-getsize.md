---
description: Ottiene le dimensioni dell'oggetto in byte.
title: IDebugObject::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df7b64065f331165e33c443f385fc79566fbb131
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043232"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
Ottiene le dimensioni dell'oggetto in byte.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSize( 
   UINT* pnSize
);
```

```csharp
int GetSize(
   out uint pnSize
);
```

## <a name="parameters"></a>Parametri
`pnSize`\
[out] Restituisce le dimensioni in byte.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Usare il [metodo GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) per recuperare il valore come sequenza di byte.

## <a name="see-also"></a>Vedi anche
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [Getvalue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
