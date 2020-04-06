---
title: IDebugEnumField::GetStringFromValue . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de59c573f7e233ea2aacb0dfa38826051c59373
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730294"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Questo metodo ottiene il nome della costante di enumerazione in base al relativo valore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetStringFromValue(
   ULONGLONG value,
   BSTR*     pbstrValue
);
```

```csharp
int GetStringFromValue(
   ulong      value,
   out string pbstrValue
);
```

## <a name="parameters"></a>Parametri
`value`\
[in] Valore per il quale ottenere il nome della costante di enumerazione.

`pbstrValue`\
[fuori] Restituisce il nome della costante di enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso `S_FALSE` contrario, restituisce se il valore non ha un nome associato o restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Se allo stesso valore è associato più di un nome, verrà restituito il nome definito nell'enumerazione.

## <a name="see-also"></a>Vedere anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
