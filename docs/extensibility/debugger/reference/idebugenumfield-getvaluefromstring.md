---
title: IDebugEnumField::GetValueFromString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromString
helpviewer_keywords:
- IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e714e6b2028605eb9c820f904cedf9ed4c23eab8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920393"
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

#### <a name="parameters"></a>Parametri
 `pszValue`

 [in] Stringa che specifica il nome per il quale ottenere il valore. Si noti che per C++, questa è una stringa di caratteri "wide".

 `pValue`

 [out] Restituisce il valore numerico associato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`, se il nome non fa parte di enumerazione o un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo è tra maiuscole e minuscole. Se è necessaria una ricerca tra maiuscole e minuscole (ad esempio, in un linguaggio, ad esempio Visual Basic in cui i nomi non sono tra maiuscole e minuscole), usare [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).

## <a name="see-also"></a>Vedere anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)