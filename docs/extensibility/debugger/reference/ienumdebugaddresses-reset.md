---
description: Questo metodo reimposta l'enumerazione addresses sul primo elemento.
title: IEnumDebugAddresses::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42d53d2d3af1853c42c51f5d990102d0db951ba81fa0c7ad6dd6d1f6e0b8981d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121415494"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
Questo metodo reimposta l'enumerazione sul primo elemento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parametri
 nessuno

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Dopo la chiamata a questo metodo, la chiamata successiva a [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) restituisce il primo elemento dell'enumerazione .

## <a name="see-also"></a>Vedi anche
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [Avanti](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
