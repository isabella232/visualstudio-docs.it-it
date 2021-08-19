---
description: Recupera il numero specificato di byte dall'oggetto .
title: IEEDataStorage::GetData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d8f646e137d5709bb49acac9074a1ad08981ffa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137886"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Recupera il numero specificato di byte dall'oggetto .

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
[in] Numero di byte da recuperare (la `data` matrice deve contenere almeno questo numero di byte).

`sizeGotten`\
[out] Restituisce il numero di byte effettivamente recuperati.

`data`\
[in, out] Matrice da riempita con i dati richiesti.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 L'uso consigliato di questo metodo è recuperare tutti i byte di dati in una matrice locale, poiché non è possibile ignorare i byte nel processo di recupero. In questo caso, il parametro `dataSize` deve essere il valore restituito dal metodo [GetSize.](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

## <a name="see-also"></a>Vedi anche
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
