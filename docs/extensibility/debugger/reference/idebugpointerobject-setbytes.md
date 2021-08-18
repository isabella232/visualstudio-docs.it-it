---
description: Imposta il valore a cui punta da una serie di byte consecutivi.
title: IDebugPointerObject::SetBytes | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c65ad63859daf50228de9b93b5f304a179e377b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122088289"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Imposta il valore a cui punta da una serie di byte consecutivi.

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
[in] Offset, in byte, dall'inizio dell'oggetto a cui punta.

`dwCount`\
[in] Numero di byte da impostare.

`pBytes`\
[in] Matrice di byte che rappresenta il nuovo valore. Questo valore viene archiviato nell'oggetto , a partire dall'offset specificato.

`pdwBytes`\
[out] Restituisce il numero di byte effettivamente impostati.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Questo metodo viene usato se il puntatore rappresentato da [questo oggetto IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o a una semplice matrice di tipi primitivi, ovvero una matrice che può essere rappresentata da una semplice sequenza di byte. Questo `IDebugPointerObject` oggetto non può essere un riferimento Null (deve puntare a un indirizzo in memoria).

## <a name="see-also"></a>Vedi anche
- [Getbytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
