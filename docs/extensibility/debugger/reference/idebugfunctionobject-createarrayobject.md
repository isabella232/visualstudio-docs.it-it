---
description: Crea un oggetto matrice.
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 822a00dcfb4b4ba6a5b9739135ae756f92d2fe7437d8f9dcc8407fd17624a2fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417262"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crea un oggetto matrice. Questa matrice può contenere valori primitivi o di istanza di oggetto.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametri
`ot`\
[in] Specifica un valore [dell'enumerazione OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) che indica il tipo del nuovo oggetto matrice.

`pClassField`\
[in] Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta la classe di un oggetto, se si crea una matrice di valori di istanza dell'oggetto. Se si crea una matrice di oggetti primitivi, questo parametro è un valore Null.

`dwRank`\
[in] Rango o numero di dimensioni della matrice.

`dwDims`\
[in] Dimensioni di ogni dimensione della matrice.

`dwLowBounds`\
[in] Origine di ogni dimensione (in genere 0 o 1).

`ppObject`\
[out] Restituisce un [oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta la matrice appena creata. Si tratta in realtà di [un oggetto IDebugArrayObject.](../../../extensibility/debugger/reference/idebugarrayobject.md)

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo per creare un oggetto che rappresenta un parametro di matrice per la funzione rappresentata [dall'interfaccia IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
