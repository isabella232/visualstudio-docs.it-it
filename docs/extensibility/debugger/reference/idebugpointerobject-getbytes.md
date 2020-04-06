---
title: Proprietà IDebugPointerObject::GetBytes . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725512"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ottiene il valore a cui punta come una serie di byte consecutivi.

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
[in] Offset, in byte, dall'inizio dell'oggetto a cui punta.

`dwCount`\
[in] Numero di byte da recuperare.

`pBytes`\
[in, out] Matrice che viene compilata con il valore come una serie di byte consecutivi, a partire dall'offset specificato dall'oggetto a cui punta.

`pdwBytes`\
[fuori] Restituisce il numero di byte recuperati effettivamente.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene utilizzato se il puntatore come rappresentato da questo [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o una matrice semplice di tipi primitivi (vale a dire, una matrice che può essere rappresentata da una semplice sequenza di byte).

## <a name="see-also"></a>Vedere anche
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetByte](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
