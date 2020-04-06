---
title: Proprietà IPropertyProxyEESide::CreateReplacementObject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715043"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crea una copia di un oggetto dati specifico dell'analizzatore di espressioni (EE).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametri
`dataIn`\
[in] Oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenente i dati da copiare.

`dataOut`\
[out] Restituisce un nuovo oggetto `IEEDataStorage`.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 A questo metodo viene assegnato un [iEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) oggetto che rappresenta una matrice di byte. Questo oggetto dati in ingresso non viene in genere implementato da EE. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato da `IEEDataStorage` EE, che consente a EE implementare l'interfaccia su qualsiasi classe desiderata.

 Si noti che i `IEEDataStorage` dati forniti dall'oggetto in `IEEDataStorage` ingresso devono essere gli stessi dati nell'oggetto in uscita.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
