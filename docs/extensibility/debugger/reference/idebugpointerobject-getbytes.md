---
description: Ottiene il valore a cui punta come una serie di byte consecutivi.
title: IDebugPointerObject::GetBytes | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34b81b01d04ea895b93153a57686a4d784d57b20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088302"
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
[in, out] Matrice compilata con il valore come serie di byte consecutivi, a partire dall'offset specificato dall'oggetto a cui punta.

`pdwBytes`\
[out] Restituisce il numero di byte effettivamente recuperati.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene usato se il puntatore rappresentato da [questo oggetto IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o a una semplice matrice di tipi primitivi, ovvero una matrice che può essere rappresentata da una semplice sequenza di byte.

## <a name="see-also"></a>Vedi anche
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
