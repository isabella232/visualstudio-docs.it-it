---
title: IEEDataStorage::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eff31ef70fc8cb812ff820a92653b6bb0cab6cd5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868224"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Restituisce il numero di byte contenuti in questo oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

#### <a name="parameters"></a>Parametri
 `size`

 [out] Il numero di byte contenuti in questo oggetto.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Usare la [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) metodo per recuperare i byte di dati effettivi.

## <a name="see-also"></a>Vedere anche
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)