---
title: Proprietà IDebugFunctionObject::CreateArrayObject . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728612"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crea un oggetto matrice. Questa matrice può contenere valori primitivi o di istanza dell'oggetto.

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
[in] Specifica un valore dall'enumerazione [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) che indica il tipo del nuovo oggetto matrice.

`pClassField`\
[in] Oggetto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta la classe di un oggetto, se si crea una matrice di valori di istanza dell'oggetto. Se si crea una matrice di oggetti primitivi, questo parametro è un valore null.

`dwRank`\
[in] Classificazione o numero di dimensioni della matrice.

`dwDims`\
[in] Dimensioni di ogni dimensione della matrice.

`dwLowBounds`\
[in] L'origine di ogni dimensione (in genere 0 o 1).

`ppObject`\
[fuori] Restituisce un [oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta la matrice appena creata. Si tratta in realtà un [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) oggetto.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Chiamare questo metodo per creare un oggetto che rappresenta un parametro di matrice per la funzione rappresentata dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
