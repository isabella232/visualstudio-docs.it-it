---
description: Questo metodo ottiene il nome della costante di enumerazione in base al relativo valore.
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692d5fd16912be8645e99fd2b54a8fbb4871b007
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035098"
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
[out] Restituisce il nome della costante di enumerazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce ; in caso contrario, restituisce se al valore non è associato `S_OK` alcun nome oppure restituisce un codice di `S_FALSE` errore.

## <a name="remarks"></a>Commenti
 Se è presente più di un nome associato allo stesso valore, verrà restituito il nome definito nell'enumerazione .

## <a name="see-also"></a>Vedi anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
