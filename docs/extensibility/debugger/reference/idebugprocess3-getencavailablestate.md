---
title: IDebugProcess3::GetENCAvailableState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99ec4ff53fe9baad2c3a36f252c652f37822ba83
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313948"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Questo metodo ottiene lo stato corrente di modifica e continuazione del processo. Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetENCAvailableState(
   EncUnavailableReason* pReason
);
```

```csharp
int GetENCAvailableState(
   EncUnavailableReason[] pReason
);
```

## <a name="parameters"></a>Parametri
`pReason`\
[out] Un valore compreso il [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.

> [!NOTE]
> Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.

## <a name="remarks"></a>Note
 Questo stato può essere influenzato dal [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).

## <a name="see-also"></a>Vedere anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)