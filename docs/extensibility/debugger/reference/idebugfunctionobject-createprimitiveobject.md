---
title: 'IDebugFunctionObject:: CreatePrimitiveObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 24b26a072a3bebda2d01a89baaf2910de96e77d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728527"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crea un oggetto dati primitivo, ad esempio un intero semplice.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametri
`ot`\
in Valore dell'enumerazione [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) che rappresenta il tipo di primitiva da creare.

`ppObject`\
out Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Chiamare questo metodo per creare un oggetto che rappresenta un oggetto primitivo che è un parametro per la funzione rappresentata dall'interfaccia [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) . Se, ad esempio, la stringa dell'espressione è "stringa (5)", questo metodo verrà usato per creare un oggetto che rappresenta il numero intero 5.

## <a name="see-also"></a>Vedere anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
