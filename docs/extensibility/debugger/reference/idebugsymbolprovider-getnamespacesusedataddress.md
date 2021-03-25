---
description: Questo metodo crea un enumeratore per gli spazi dei nomi associati all'indirizzo di debug.
title: 'IDebugSymbolProvider:: GetNamespacesUsedAtAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e9f09749cfb3495e71d9cbacfd4a9d430acc107
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087015"
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
Questo metodo crea un enumeratore per gli spazi dei nomi associati all'indirizzo di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetNamespacesUsedAtAddress( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetNamespacesUsedAtAddress(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
in Indirizzo di debug.

`ppEnum`\
out Restituisce un enumeratore [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) per gli spazi dei nomi.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 È possibile che siano presenti diversi spazi dei nomi associati a un determinato indirizzo di debug, ad esempio spazi dei nomi annidati o più `using` istruzioni.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
