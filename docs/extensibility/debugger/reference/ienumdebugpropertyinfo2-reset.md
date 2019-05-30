---
title: IEnumDebugPropertyInfo2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Reset
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Reset
ms.assetid: fa4201c1-4633-4596-93aa-bd415c4ed71a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 050eb3e88789a9f028ad0fb11bf32abacb92348d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347172"
---
# <a name="ienumdebugpropertyinfo2reset"></a>IEnumDebugPropertyInfo2::Reset
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
 Dopo che questo metodo viene chiamato, la chiamata successiva per la [successivo](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) metodo restituisce il primo elemento dell'enumerazione.

## <a name="see-also"></a>Vedere anche
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)