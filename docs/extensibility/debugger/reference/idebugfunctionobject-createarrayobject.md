---
description: Crea un oggetto Array.
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
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
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94216521f0a57a76f83c68f168ed1afcac199a0e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073547"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crea un oggetto Array. Questa matrice può contenere valori di istanze primitive o di oggetti.

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
in Specifica un valore dell'enumerazione [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) che indica il tipo del nuovo oggetto matrice.

`pClassField`\
in Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta la classe di un oggetto, se si crea una matrice di valori di istanza dell'oggetto. Se si crea una matrice di oggetti primitivi, questo parametro è un valore null.

`dwRank`\
in Rango o numero di dimensioni della matrice.

`dwDims`\
in Dimensioni di ogni dimensione della matrice.

`dwLowBounds`\
in Origine di ogni dimensione (in genere 0 o 1).

`ppObject`\
out Restituisce un oggetto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta la matrice appena creata. Si tratta in realtà di un oggetto [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo per creare un oggetto che rappresenta un parametro di matrice per la funzione rappresentata dall'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
