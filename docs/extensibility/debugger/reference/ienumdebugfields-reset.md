---
description: Questo metodo reimposta l'enumerazione dei campi sul primo elemento.
title: IEnumDebugFields::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34448e389b545a3fe1d4ba7d86cbbe753567876606a4cae25118a573dfca3263
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360248"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Questo metodo reimposta l'enumerazione sul primo elemento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

#### <a name="parameters"></a>Parametri
 nessuno

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Dopo la chiamata a questo metodo, la chiamata successiva a [Next](../../../extensibility/debugger/reference/ienumdebugfields-next.md) restituisce il primo elemento dell'enumerazione .

## <a name="see-also"></a>Vedi anche
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
