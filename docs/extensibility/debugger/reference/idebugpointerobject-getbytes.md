---
description: Ottiene il valore a cui punta una serie di byte consecutivi.
title: 'IDebugPointerObject:: GetBytes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4a150f819610de97ee292302d89e2007c6235aae
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087626"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ottiene il valore a cui punta una serie di byte consecutivi.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>Parametri
`dwStart`\
in Offset, in byte, dall'inizio dell'oggetto a cui puntava.

`dwCount`\
in Numero di byte da recuperare.

`pBytes`\
[in, out] Matrice compilata con il valore come una serie di byte consecutivi, a partire dall'offset specificato dall'oggetto a cui fa riferimento.

`pdwBytes`\
out Restituisce il numero di byte effettivamente recuperati.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene utilizzato se il puntatore rappresentato da questo [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o a una semplice matrice di tipi primitivi (ovvero una matrice che può essere rappresentata da una semplice sequenza di byte).

## <a name="see-also"></a>Vedi anche
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
