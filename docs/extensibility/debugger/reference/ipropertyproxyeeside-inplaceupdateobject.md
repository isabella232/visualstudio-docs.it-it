---
description: Aggiorna i dati dell'oggetto con l'oggetto dati specificato e restituisce un nuovo oggetto dati che rappresenta i nuovi dati dell'oggetto.
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27826db10e6ef7265416d83cf37fb38c0706c452076223e7027b0ef1a7034f58
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388955"
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
[out] Restituisce un nuovo `IEEDataStorage` oggetto contenente i dati sostituiti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo aggiorna effettivamente i dati dell'oggetto. Non è necessario che i dati nell'oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) restituito siano uguali ai dati nell'oggetto in ingresso, ma l'oggetto restituito deve riflettere il valore `IEEDataStorage` corrente della proprietà.

 L'oggetto dati in ingresso non viene in genere implementato dal edizione Enterprise. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato dal edizione Enterprise, che consente al edizione Enterprise di implementare l'interfaccia su qualsiasi `IEEDataStorage` classe desiderata.

 Il [metodo CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crea un oggetto dati basato sull'oggetto dati in ingresso, ma non influisce sui dati originali della proprietà.

## <a name="see-also"></a>Vedi anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
