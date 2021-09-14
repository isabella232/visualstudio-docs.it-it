---
description: Questo metodo ottiene le informazioni sulla richiesta del punto di interruzione che descrivono questa richiesta del punto di interruzione.
title: IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c889b73f231b2e31bc60be7bc5d1700b3a891ba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636444"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Questo metodo ottiene le informazioni sulla richiesta del punto di interruzione che descrivono questa richiesta del punto di interruzione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetRequestInfo2(
   BPREQI_FIELDS      dwFields,
   BP_REQUEST_INFO2*  bBPRequestInfo
);
```

```csharp
int GetRequestInfo2(
   enum_BPREQI_FIELDS  dwFields,
   BP_REQUEST_INFO2[]  bBPRequestInfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di flag [dell'BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) che determinano quali campi di devono `pBPRequestInfo` essere compilati.

`bBPRequestInfo`\
[out] Struttura [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) da riempita.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 In questa richiesta sono presenti più informazioni di quelle restituite dal [metodo GetRequestInfo.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)

## <a name="see-also"></a>Vedi anche
- [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
