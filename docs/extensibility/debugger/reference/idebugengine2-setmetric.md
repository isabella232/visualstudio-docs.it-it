---
description: Questo metodo imposta un valore del Registro di sistema noto come metrica.
title: Interfaccia IDebugEngine2::SetMetric | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5e32147a03f80a00e7c87091d09cbfd447ee71edd8af9ef60ae0a5a863e4d214
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390040"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Questo metodo imposta un valore del Registro di sistema noto come metrica.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
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
[in] Nome della metrica.

`varValue`\
[in] Specifica il valore della metrica.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Una metrica è un valore del Registro di sistema usato per modificare il comportamento di un motore di debug o per annunciare le funzionalità supportate. Questo metodo può inoltrare la chiamata al formato appropriato degli [helper SDK per la funzione di](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) debug, `SetMetric` .

## <a name="see-also"></a>Vedi anche
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
