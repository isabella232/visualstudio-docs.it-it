---
title: 'IDebugField:: GetType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dbfb21abc8feaa95a8842707a56add513eaa6875
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869804"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
Questo metodo ottiene il tipo di campo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetType( 
   IDebugField** ppType
);
```

```csharp
int GetType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Parametri
`ppType`\
out Restituisce il tipo di campo come un altro oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
