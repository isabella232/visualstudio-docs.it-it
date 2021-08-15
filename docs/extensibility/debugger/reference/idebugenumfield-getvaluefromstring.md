---
description: Questo metodo restituisce il valore associato al nome di una costante di enumerazione.
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3060fafd2c887dd79933bb1baa04644d77a1113a132c3d751b31332c7643d526
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360508"
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Questo metodo restituisce il valore associato al nome di una costante di enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetValueFromString(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromString(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parametri
`pszValue`\
[in] Stringa che specifica il nome per il quale ottenere il valore. Si noti che per C++ si tratta di una stringa di caratteri wide.

`pValue`\
[out] Restituisce il valore numerico associato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce ; in caso contrario, restituisce , se il nome non fa parte dell'enumerazione `S_OK` o un codice di `S_FALSE` errore.

## <a name="remarks"></a>Commenti
 Questo metodo fa distinzione tra maiuscole e minuscole. Se è necessaria una ricerca senza distinzione tra maiuscole e minuscole, ad esempio in un linguaggio come Visual Basic in cui per i nomi non viene fatto distinzione tra maiuscole e minuscole, usare [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Vedi anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)
