---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 25becdae62dbdda78e04404528eeb099a4914265
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212400"
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Questo metodo ottiene il nome della costante di enumerazione dato il relativo valore.

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
[in] Il valore per il quale ottenere il nome dell'enumerazione costante.

`pbstrValue`\
[out] Restituisce il nome della costante di enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` se il valore non ha associato un nome, o restituisce un codice di errore.

## <a name="remarks"></a>Note
 Se è presente più di un nome associato lo stesso valore, verrà restituito il nome definito nell'enumerazione.

## <a name="see-also"></a>Vedere anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)