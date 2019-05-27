---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f35c63310abe227dd50428d34122787ed0fb292
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212618"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Crea un oggetto matrice. Questa matrice può contenere una primitiva o i valori dell'istanza dell'oggetto.

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
[in] Specifica un valore di [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumerazione che indica il tipo del nuovo oggetto matrice.

`pClassField`\
[in] Un' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) oggetto che rappresenta la classe di un oggetto, se la creazione di una matrice di oggetti i valori dell'istanza. Se si crea una matrice di oggetti primitivi, questo parametro è un valore null.

`dwRank`\
[in] Il numero di dimensioni o il numero di dimensioni della matrice.

`dwDims`\
[in] Le dimensioni di ogni dimensione della matrice.

`dwLowBounds`\
[in] L'origine di ogni dimensione (in genere 0 o 1).

`ppObject`\
[out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta la matrice appena creata. Si tratta in realtà un' [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) oggetto.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Chiamare questo metodo per creare un oggetto che rappresenta un parametro di matrice per la funzione che è rappresentata dal [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)