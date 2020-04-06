---
title: Proprietà IEEDataStorage::GetData . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718206"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera il numero specificato di byte dall'oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Parametri
`dataSize`\
[in] Il numero di byte `data` da recuperare (la matrice deve contenere almeno questo numero di byte).

`sizeGotten`\
[fuori] Restituisce il numero di byte recuperati effettivamente.

`data`\
[in, out] Array da compilare con i dati richiesti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 L'utilizzo consigliato di questo metodo consiste nel recuperare tutti i byte di dati in una matrice locale, poiché non è possibile ignorare i byte nel processo di recupero. In questo caso, `dataSize` il parametro deve essere il valore restituito dal [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) metodo.

## <a name="see-also"></a>Vedere anche
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
