---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e54a7f38eed85ffe2757b373de1af59e1aaa126b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842717"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Imposta il valore indicato da una serie di byte consecutivi.

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

#### <a name="parameters"></a>Parametri
 `dwStart`

 [in] Offset, in byte, dall'inizio dell'oggetto puntato.

 `dwCount`

 [in] Il numero di byte da impostare.

 `pBytes`

 [in] Matrice di byte che rappresenta il nuovo valore. Questo valore viene archiviato nell'oggetto, a partire dall'offset specificato.

 `pdwBytes`

 [out] Restituisce che il numero di byte effettivamente impostato.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Questo metodo viene utilizzato se il puntatore come rappresentato da questo [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o di una semplice matrice di tipi primitivi (vale a dire, una matrice che può essere rappresentato da una semplice sequenza di byte). Ciò `IDebugPointerObject` oggetto non può essere un riferimento null (deve puntare a un indirizzo in memoria).

## <a name="see-also"></a>Vedere anche
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)