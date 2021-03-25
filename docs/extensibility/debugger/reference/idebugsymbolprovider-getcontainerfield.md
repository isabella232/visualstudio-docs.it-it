---
description: Questo metodo ottiene il campo che contiene l'indirizzo di debug.
title: 'IDebugSymbolProvider:: GetContainerField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df00b0900d36a09931fb46d4774e55cd2117c922
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087119"
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
Questo metodo ottiene il campo che contiene l'indirizzo di debug.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetContainerField( 
   IDebugAddress*         pAddress,
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainerField(
   IDebugAddress            pAddress,
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Parametri
`pAddress`\
in Indirizzo rappresentato da un'interfaccia [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`ppContainerField`\
out Restituisce un campo contenitore rappresentato da un'interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
