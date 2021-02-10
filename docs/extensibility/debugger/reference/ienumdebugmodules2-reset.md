---
title: 'IEnumDebugModules2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fdc98e9ac2d545670fde240cea914be9108b8f0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956256"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
Reimposta l'enumerazione sul primo elemento.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Dopo la chiamata a questo metodo, la chiamata successiva al metodo [successivo](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) restituisce il primo elemento dell'enumerazione.

## <a name="see-also"></a>Vedi anche
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
