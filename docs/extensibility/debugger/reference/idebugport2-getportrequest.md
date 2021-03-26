---
description: Ottiene la descrizione di una porta utilizzata in precedenza per creare la porta, se disponibile.
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77224f98d953b61529ffed083e7be4cee0ed662f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087483"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Ottiene la descrizione di una porta utilizzata in precedenza per creare la porta, se disponibile.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parametri
`ppRequest`\
out Restituisce un oggetto [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) che rappresenta la richiesta utilizzata per creare la porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  Restituisce `E_PORT_NO_REQUEST` se non è stata creata alcuna porta utilizzando una richiesta di porta [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
