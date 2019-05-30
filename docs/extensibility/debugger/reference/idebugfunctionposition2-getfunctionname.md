---
title: IDebugFunctionPosition2::GetFunctionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionPosition2::GetFunctionName
helpviewer_keywords:
- IDebugFunctionPosition2::GetFunctionName
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3bef8ebf82786212552421ebb608e26a6708623
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313338"
---
# <a name="idebugfunctionposition2getfunctionname"></a>IDebugFunctionPosition2::GetFunctionName
Ottiene il nome della funzione a cui fa riferimento questa posizione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetFunctionName( 
   BSTR* pbstrFunctionName
);
```

```csharp
int GetFunctionName(
   out string pbstrFunctionName
);
```

## <a name="parameters"></a>Parametri
`pbstrFunctionName`\
[out] Restituisce il nome della funzione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)