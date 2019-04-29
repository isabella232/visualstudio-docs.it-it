---
title: IEnumDebugCustomAttributes::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c25d2dc63002d41d49e6bdac8a106217ff49e277
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62914934"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
Riporta all'inizio la sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Dopo che questo metodo viene chiamato, la chiamata successiva per la [successivo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) metodo restituisce il primo elemento dell'enumerazione.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [avanti](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)