---
description: Questo metodo restituisce un proxy per un oggetto Property.
title: 'IEEVisualizerService:: GetPropertyProxy | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetPropertyProxy
helpviewer_keywords:
- IEEVisualizerService::GetPropertyProxy method
ms.assetid: 748750f4-76e7-4580-9da2-afba07681b37
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0be668c369143509c000cee767d302b83ba6287
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086846"
---
# <a name="ieevisualizerservicegetpropertyproxy"></a>IEEVisualizerService::GetPropertyProxy
Questo metodo restituisce un proxy per un oggetto Property.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetPropertyProxy(
   DWORD                  dwID,
   IPropertyProxyEESide** proxy
);
```

```csharp
int GetPropertyProxy(
   uint                     dwID,
   out IPropertyProxyEESide proxy
);
```

## <a name="parameters"></a>Parametri
`dwID`\
in ID del proxy di proprietà da recuperare.

`proxy`\
out Proxy desiderato implementato in un'interfaccia [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
- [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) passa la richiesta a questo metodo come parte del supporto per i visualizzatori di tipi.

## <a name="see-also"></a>Vedi anche
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)
