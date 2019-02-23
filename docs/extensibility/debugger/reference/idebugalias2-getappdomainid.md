---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 890e215c7e575e67a4360717851bab538966f419
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715050"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera l'identificatore per il dominio applicazione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

#### <a name="parameters"></a>Parametri
 `pappDomainId`

 [out] Restituisce l'identificatore del dominio applicazione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Viene creato un nuovo dominio applicazione e le modifiche di identificatore di dominio dell'applicazione ogni volta che l'applicazione viene riavviata.

## <a name="see-also"></a>Vedere anche
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)