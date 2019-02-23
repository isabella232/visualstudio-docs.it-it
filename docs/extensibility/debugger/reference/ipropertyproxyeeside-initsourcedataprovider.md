---
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fb0d2b960c2bafd1a2d502e41c8a435a5205d11
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687484"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inizializza i dati di origine per questo oggetto e restituisce un oggetto contenente i dati iniziali.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

#### <a name="parameters"></a>Parametri
 `dataOut`

 [out] Restituisce un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo esegue tutte le operazioni necessarie per inizializzare un oggetto in modo che venga restituito un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) interfaccia sui dati dell'oggetto. Ciò consente di essere visualizzate e, se consentito, modificato da un visualizzatore di tipi di dati dell'oggetto.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)