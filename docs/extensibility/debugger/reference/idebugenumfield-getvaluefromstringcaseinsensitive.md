---
title: IDebugEnumField::GetValueFromStringCaseInsensitive . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 551945ded9d1ba3e973f18c21463a896cbd478c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730249"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Questo metodo utilizza una ricerca senza distinzione tra maiuscole e minuscole per restituire il valore associato al nome di una costante di enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetValueFromStringCaseInsensitive(
   LPCOLESTR  pszValue,
   ULONGLONG* pvalue
);
```

```csharp
int GetValueFromStringCaseInsensitive(
   string    pszValue,
   out ulong pValue
);
```

## <a name="parameters"></a>Parametri
`pszValue`\
[in] Stringa che specifica il nome per il quale ottenere il valore. Si noti che per c'è, si tratta di una stringa di caratteri di tipo wide.

`pValue`\
[fuori] Restituisce il valore numerico associato.

## <a name="return-value"></a>Valore restituito
 Se ha `S_OK`esito positivo, restituisce ; in caso `S_FALSE`contrario, restituisce , se il nome non fa parte dell'enumerazione o un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo non fa distinzione tra maiuscole e minuscole. Se è necessaria una ricerca con distinzione tra maiuscole e minuscole (ad esempio, in un linguaggio, ad esempio, in C, dove i nomi fanno distinzione tra maiuscole e minuscole), utilizzare [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).

## <a name="see-also"></a>Vedere anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
