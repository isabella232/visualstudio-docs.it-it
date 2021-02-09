---
title: 'IDebugPort2:: GetPortRequest | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2694a0ee6e134a5f822c0f84284d96b7ce57ef93
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907884"
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
