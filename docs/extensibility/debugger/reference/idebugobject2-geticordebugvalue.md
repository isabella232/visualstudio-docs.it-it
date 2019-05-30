---
title: IDebugObject2::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edbacbaeac9a5172d8c3bb5b54ee38fff201a2bf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317359"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Ottiene un oggetto di codice gestito che rappresenta il valore associato all'oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parametri
`ppUnk`\
[out] `IUnknown` interfaccia che rappresenta l'alias. Questa interfaccia è possibile eseguire query per il `ICorDebugValue` interfaccia.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Il `ICorDebugValue` oggetto è un'interfaccia di Common Language Runtime che rappresenta un valore.

## <a name="see-also"></a>Vedere anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)