---
description: Imposta il valore a cui punta una serie di byte consecutivi.
title: 'IDebugPointerObject:: sebytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 015a7782fae01f06a9d1cc4a5e64090303d2f2e0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087587"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Imposta il valore a cui punta una serie di byte consecutivi.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>Parametri
`dwStart`\
in Offset, in byte, dall'inizio dell'oggetto a cui puntava.

`dwCount`\
in Numero di byte da impostare.

`pBytes`\
in Matrice di byte che rappresenta il nuovo valore. Questo valore viene archiviato nell'oggetto, a partire dall'offset specificato.

`pdwBytes`\
out Restituisce il numero di byte effettivamente impostati.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene utilizzato se il puntatore rappresentato da questo [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o a una semplice matrice di tipi primitivi (ovvero una matrice che può essere rappresentata da una semplice sequenza di byte). Questo `IDebugPointerObject` oggetto non può essere un riferimento null (deve puntare a un indirizzo in memoria).

## <a name="see-also"></a>Vedi anche
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
