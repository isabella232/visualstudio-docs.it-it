---
title: IEnumDebugFields::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6bf669261a3ece31e452227b7c93d7ce8bf07c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914635"
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
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Dopo che questo metodo viene chiamato, la chiamata successiva a [successivo](../../../extensibility/debugger/reference/ienumdebugfields-next.md) restituisce il primo elemento dell'enumerazione.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [avanti](../../../extensibility/debugger/reference/ienumdebugfields-next.md)