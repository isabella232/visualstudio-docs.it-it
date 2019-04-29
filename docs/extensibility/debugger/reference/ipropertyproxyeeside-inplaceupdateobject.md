---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8617dd6f37d7e90d23c3ed454ef56122b36f6b75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913949"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Aggiorna i dati dell'oggetto con l'oggetto dati specificato e restituisce un nuovo oggetto dati che rappresenta i dati dell'oggetto nuovo.

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

#### <a name="parameters"></a>Parametri
 `dataIn`

 [in] Un' [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto contenente i nuovi dati.

 `dataOut`

 [out] Restituisce un nuovo `IEEDataStorage` oggetto contenente i dati sostituiti.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo aggiorna effettivamente i dati dell'oggetto. I dati nell'oggetto restituito [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto non deve essere quello utilizzato per i dati in ingresso `IEEDataStorage` oggetto, ma l'oggetto restituito deve riflettere il valore della proprietà corrente.

 L'oggetto dati in entrata non è in genere implementato dal motore di esecuzione. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato dal motore di esecuzione, che consente di implementare EE il `IEEDataStorage` interfaccia su qualsiasi classe desiderata.

 Il [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) metodo crea un oggetto dati in base all'oggetto dati in ingresso, ma influisce sui dati originali della proprietà.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)