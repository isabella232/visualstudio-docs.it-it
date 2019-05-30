---
title: IDebugMemoryContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee8dd65a3bcaef7fd5a23da6c2a5f9c21a4838af
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347000"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
Recupera il nome visualizzabile dall'utente per questo contesto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>Parametri
`pbstrName`\
[out] Restituisce il nome del contesto di memoria.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il nome di un contesto di memoria non è in genere utilizzato.

## <a name="see-also"></a>Vedere anche
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)