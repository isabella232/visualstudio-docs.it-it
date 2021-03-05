---
description: Questo metodo ottiene le informazioni sulla richiesta del punto di interruzione che descrivono la richiesta del punto di interruzione.
title: 'IDebugBreakpointRequest3:: GetRequestInfo2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0d62b684fd171857870f59b2f3eec2e034cab11
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162329"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Questo metodo ottiene le informazioni sulla richiesta del punto di interruzione che descrivono la richiesta del punto di interruzione.

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
in Combinazione di flag dell'enumerazione [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) che determinano i campi da `pBPRequestInfo` compilare.

`bBPRequestInfo`\
out Struttura di [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) da compilare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore.

## <a name="remarks"></a>Commenti
 Sono disponibili altre informazioni in questa richiesta rispetto a quelle restituite dal metodo [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
