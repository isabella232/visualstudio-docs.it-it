---
title: IDebugProcess3::DisableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3ee29540a11248a299d65c32cf2c8396b1fa2ef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314053"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Questo metodo in modo esplicito Disabilita modifica e continuazione su questo processo (e tutti i programmi contengono). Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametri
`reason`\
[in] Un valore compreso il [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumerazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.

> [!NOTE]
> Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL`.

## <a name="remarks"></a>Note
 Una volta modifica e continuazione è disabilitata per un processo, può essere abilitato nuovamente solo riavviando il processo.

## <a name="see-also"></a>Vedere anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)