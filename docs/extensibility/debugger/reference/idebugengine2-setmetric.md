---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10e4662536dbe8fef8c250122d22520df1736cf8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352573"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Questo metodo imposta un valore del Registro di sistema noto come una metrica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parametri
`pszMetric`\
[in] Il nome della metrica.

`varValue`\
[in] Specifica il valore della metrica.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Una metrica è un valore del Registro di sistema utilizzato per modificare il comportamento del motore di debug o per annunciare le funzionalità supportate. Questo metodo può inoltrare la chiamata alla forma appropriata del [helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) funzione `SetMetric`.

## <a name="see-also"></a>Vedere anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)