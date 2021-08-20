---
description: Restituisce il numero di byte contenuti in questo oggetto .
title: IEEDataStorage::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b0de358f2f207da7586c09be094ec14f6dadfbf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095790"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Restituisce il numero di byte contenuti in questo oggetto .

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

## <a name="parameters"></a>Parametri
`size`\
[out] Numero di byte contenuti in questo oggetto .

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Usare il [metodo GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) per recuperare i byte di dati effettivi.

## <a name="see-also"></a>Vedi anche
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
