---
title: 'IDebugAlias2:: GetAppDomainId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c50473e12399e3977de55e67c7251d5783eecfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947125"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera l'identificatore per il dominio dell'applicazione.

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

## <a name="parameters"></a>Parametri
`pappDomainId`\
out Restituisce l'identificatore del dominio dell'applicazione.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'identificatore di dominio dell'applicazione cambia ogni volta che l'applicazione viene riavviata e viene creato un nuovo dominio applicazione.

## <a name="see-also"></a>Vedi anche
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
