---
description: Crea un oggetto dati primitivo, ad esempio un integer semplice.
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 49c39665098eb37563ae9b6421d64a30b215921fb08ab118a47b5f443c793959
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121402753"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Crea un oggetto dati primitivo, ad esempio un integer semplice.

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
[in] Valore [dell'enumerazione OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) che rappresenta il tipo di primitiva da creare.

`ppObject`\
[out] Restituisce un [oggetto IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) che rappresenta l'oggetto appena creato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Chiamare questo metodo per creare un oggetto che rappresenta un oggetto primitivo che è un parametro della funzione rappresentata [dall'interfaccia IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md) Ad esempio, se la stringa dell'espressione è "myString(5)", questo metodo verrà usato per creare un oggetto che rappresenta il numero intero 5.

## <a name="see-also"></a>Vedi anche
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
