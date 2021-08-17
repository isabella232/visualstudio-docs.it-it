---
description: Questo metodo ottiene il tipo di campo.
title: IDebugField::GetType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68bfc7654824285e6fe99d51e17dbf9f73e67c914786b3a03459cb9506b0b207
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417249"
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
[out] Restituisce il tipo di campo come un altro [oggetto IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
