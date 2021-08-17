---
description: Questo metodo restituisce un oggetto IDebugField che rappresenta il nome dell'enumerazione.
title: IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f5cb3be55e76e1471836bbd422367d637d6b12b93ee5099fc5a70705821f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342206"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Questo metodo restituisce un [oggetto IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il nome dell'enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>Parametri
`ppField`\
[out] Restituisce [L'oggetto IDebugField che](../../../extensibility/debugger/reference/idebugfield.md) descrive il nome di questa enumerazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Il nome dell'enumerazione contiene anche il tipo dell'enumerazione , associato a una posizione di memoria tramite [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="see-also"></a>Vedi anche
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Associare](../../../extensibility/debugger/reference/idebugbinder-bind.md)
