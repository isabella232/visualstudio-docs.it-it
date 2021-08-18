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
ms.openlocfilehash: 6af1b13fb48f29140ccb5a76f944c48909246a34
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035241"
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
