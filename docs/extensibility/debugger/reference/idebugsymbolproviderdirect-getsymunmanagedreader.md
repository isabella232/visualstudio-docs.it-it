---
title: IDebugSymbolProviderDirect::GetSymUnmanagedReader | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetSymUnmanagedReader
- IDebugSymbolProviderDirect::GetSymUnmanagedReader
ms.assetid: 147bacfa-f66c-43e0-8a72-e601058dc57f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d2fb5a2fd5d8ba34112e01da07fc1f41177e8e9f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320407"
---
# <a name="idebugsymbolproviderdirectgetsymunmanagedreader"></a>IDebugSymbolProviderDirect::GetSymUnmanagedReader
Recupera un lettore di simboli per codice non gestito.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSymUnmanagedReader (
   ULONG32    ulAppDomainID,
   GUID       guidModule,
   IUnknown** ppSymUnmanagedReader
);
```

```csharp
int GetSymUnmanagedReader (
   uint       ulAppDomainID,
   Guid       guidModule,
   out object ppSymUnmanagedReader
);
```

## <a name="parameters"></a>Parametri
`ulAppDomainID`\
[in] Identificatore del dominio dell'applicazione.

`guidModule`\
[in] Identificatore univoco del modulo.

`ppSymUnmanagedReader`\
[out] Restituisce un oggetto che rappresenta il lettore di simboli per codice non gestito.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)