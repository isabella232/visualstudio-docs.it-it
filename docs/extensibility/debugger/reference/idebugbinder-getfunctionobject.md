---
description: Questo metodo ottiene un oggetto IDebugFunctionObject usato per creare i parametri della funzione.
title: 'IDebugBinder:: GetFunctionObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7bbcb8dba1593de824a5a0bb2d4d31f7602eb879
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067465"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Questo metodo ottiene un oggetto [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) usato per creare i parametri della funzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parametri
`ppFunction`\
out Restituisce l'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) utilizzata per creare parametri di funzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
