---
title: IEnumDebugModules2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b969b03c955368415d2e5911eb46731d133abad3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350330"
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
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Dopo che questo metodo viene chiamato, la chiamata successiva per la [successivo](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) metodo restituisce il primo elemento dell'enumerazione.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)