---
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5cfd425e6b992d8d933edd45f27d6fb4c8161a1a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891046"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Questo metodo Disabilita in modo esplicito modifica e continuazione in questo processo e in tutti i programmi in esso contenuti. Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL` .

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametri
`reason`\
in Valore dell'enumerazione [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

> [!NOTE]
> Un fornitore di porte personalizzato deve sempre restituire `E_NOTIMPL` .

## <a name="remarks"></a>Commenti
 Quando modifica e continuazione è disabilitato per un processo, può essere riabilitato solo riavviando il processo.

## <a name="see-also"></a>Vedi anche
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
