---
title: Proprietà IPropertyProxyEESide::InPlaceUpdateObject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714897"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aggiorna i dati dell'oggetto con l'oggetto dati specificato e restituisce un nuovo oggetto dati che rappresenta i nuovi dati dell'oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametri
`dataIn`\
[in] Oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenente i nuovi dati.

`dataOut`\
[fuori] Restituisce `IEEDataStorage` un nuovo oggetto contenente i dati sostituiti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo aggiorna effettivamente i dati dell'oggetto. Non è necessario che i dati nell'oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) restituito siano `IEEDataStorage` uguali ai dati nell'oggetto in ingresso, ma l'oggetto restituito deve riflettere il valore corrente della proprietà.

 L'oggetto dati in ingresso non viene in genere implementato da EE. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato da `IEEDataStorage` EE, che consente a EE implementare l'interfaccia su qualsiasi classe desiderata.

 Il [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) metodo crea un oggetto dati basato sull'oggetto dati in ingresso, ma non influisce sui dati originali della proprietà.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
