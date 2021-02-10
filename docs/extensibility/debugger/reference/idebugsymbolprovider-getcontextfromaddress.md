---
title: 'IDebugSymbolProvider:: GetContextFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContextFromAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetContextFromAddress method
ms.assetid: 7a27d56f-20d4-4e5c-af7b-7307d3aff0a1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 60ee6773e468c1f647a78712bbdcb5b64f8d6871
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954761"
---
# <a name="idebugsymbolprovidergetcontextfromaddress"></a>IDebugSymbolProvider::GetContextFromAddress
Questo metodo esegue il mapping di un indirizzo di debug in un contesto di documento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetContextFromAddress( 
   IDebugAddress*           pAddress,
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetContextFromAddress(
   IDebugAddress              pAddress,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
in Indirizzo di debug come rappresentato da un'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`ppDocContext`\
out Restituisce un contesto del documento come rappresentato da un'interfaccia [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
