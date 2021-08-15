---
description: Questo metodo ottiene un oggetto IDebugFunctionObject usato per creare i parametri della funzione.
title: Interfaccia IDebugBinder::GetFunctionObject | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5fbd978bf415565c4fab016d08bbe50729124fb2683141acdcba611659bd07a1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121342596"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Questo metodo ottiene un [oggetto IDebugFunctionObject usato](../../../extensibility/debugger/reference/idebugfunctionobject.md) per creare i parametri della funzione.

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
[out] Restituisce [l'interfaccia IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) usata per creare i parametri della funzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
