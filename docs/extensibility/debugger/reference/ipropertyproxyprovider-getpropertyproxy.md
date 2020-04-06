---
title: Proprietà IPropertyProxyProvider::GetPropertyProxy . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35c23fc56c883845bdb7fb73daa60a845ee5e21a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714832"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
Recupera l'interfaccia del proxy di proprietà per l'ID proxy specificato.

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
[in] ID del proxy di proprietà desiderato.

`proxy`\
[fuori] Restituisce un oggetto [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Per supportare i visualizzatori di tipo esterno, questo metodo in genere inoltra la chiamata al [Metodo GetPropertyProxy.](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) Vedere Visualizzazione e visualizzazione dei dati per informazioni dettagliate su come viene ottenuto il IEEVisualizerService.See [Visualizing](../../../extensibility/debugger/visualizing-and-viewing-data.md) and Viewing Data for details on how the IEEVisualizerService is obtained.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
