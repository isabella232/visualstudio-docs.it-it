---
description: Recupera l'interfaccia proxy di proprietà per l'ID proxy specificato.
title: IPropertyProxyProvider::GetPropertyProxy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider::GetPropertyProxy
helpviewer_keywords:
- IPropertyProxyProvider::GetPropertyProxy
ms.assetid: 3ebb7515-5bfe-48f4-9b8d-721b8f664eb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13c09c3755a71342544bf18bc0b8836b19aec6acbd25917b44c4efd6d325d3a7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321363"
---
# <a name="ipropertyproxyprovidergetpropertyproxy"></a>IPropertyProxyProvider::GetPropertyProxy
Recupera l'interfaccia proxy di proprietà per l'ID proxy specificato.

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
[out] Restituisce un [oggetto IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Per supportare i visualizzatori di tipi esterni, questo metodo in genere inoltra la chiamata al [metodo GetPropertyProxy.](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md) Per [informazioni dettagliate su come](../../../extensibility/debugger/visualizing-and-viewing-data.md) viene ottenuto IEEVisualizerService, vedere Visualizzazione e visualizzazione dei dati.

## <a name="see-also"></a>Vedi anche
- [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [Visualizzazione di tipi e dati](../../../extensibility/debugger/visualizing-and-viewing-data.md)
